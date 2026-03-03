# Post-Compromise Enumeration

After gaining initial access to a domain-joined machine, enumerate the AD environment to map out targets, privileges, and attack paths.

## Goals

- Identify domain admins and high-value targets
- Map group memberships and permissions
- Find misconfigured shares, GPOs, and trust relationships
- Discover paths to domain admin

## Key Tools

| Tool | Purpose |
|------|---------|
| PowerView | PowerShell-based AD enumeration |
| BloodHound | Visual attack path mapping |
| ldapdomaindump | Quick LDAP-based domain dump |
| PlumHound | BloodHound report automation |

## General Approach

1. Run ldapdomaindump for a quick overview
2. Use PowerView for targeted queries
3. Run BloodHound/SharpHound for full attack path analysis
