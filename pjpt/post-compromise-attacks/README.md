# Post-Compromise Attacks

Attacks to escalate privileges and move laterally after gaining initial access to a domain environment.

## Attack Categories

| Attack | When to Use |
|--------|-------------|
| Pass the Hash / Password | Have credentials or hashes, want lateral movement |
| Token Impersonation | Have local admin, want to steal logged-in user tokens |
| Kerberoasting | Want to crack service account passwords offline |
| GPP/cPassword | Domain-joined machine, check for stored Group Policy creds |
| URL File Attacks | Have write access to a file share |
| Mimikatz | Local admin on a machine, want to dump all credentials |
| Golden Ticket | Have krbtgt hash, want persistent domain-wide access |
| PrintNightmare | Unpatched print spooler for quick SYSTEM access |
| ZeroLogon | Unpatched DC for domain admin (dangerous -- can break DC) |

## General Notes

- Always check what you can do with current access before escalating
- Document every credential and hash you capture
- Token impersonation and Mimikatz require local admin
- Golden Ticket is a persistence technique -- save for maintaining access
