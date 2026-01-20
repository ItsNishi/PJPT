# IPv6 Attacks Overview

## Why IPv6 Matters

- Many networks have IPv6 enabled but not monitored
- Security tools often focus on IPv4
- Can bypass IPv4-only security controls

## Common Attacks

### mitm6

Tool for exploiting IPv6 in Windows networks.

```bash
# Basic usage
mitm6 -d domain.local
```

Combined with ntlmrelayx for credential capture.

### DHCPv6 Spoofing

- Windows prefers IPv6 over IPv4
- Attacker advertises as DHCPv6 server
- Can redirect DNS queries

## Mitigation

- Disable IPv6 if not needed
- Monitor IPv6 traffic
- Block DHCPv6 at network level if unused
