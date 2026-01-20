# Networking

## TCP vs UDP

| Protocol | Type | Use Cases |
|----------|------|-----------|
| TCP | Connection-oriented | High reliability needed |
| UDP | Connectionless | Streaming, DNS, VoIP |

## TCP Three-Way Handshake

1. Client sends **SYN**
2. Server responds **SYN-ACK**
3. Client sends **ACK**

Important for understanding scanning behavior.

## Common Ports

### TCP

| Port | Service | Notes |
|------|---------|-------|
| 21 | FTP | File transfer |
| 22 | SSH | Secure shell |
| 23 | Telnet | Unencrypted remote access |
| 25 | SMTP | Email |
| 53 | DNS | Name resolution |
| 80 | HTTP | Web |
| 110 | POP3 | Email retrieval |
| 139 | SMB | File sharing (NetBIOS) |
| 143 | IMAP | Email |
| 443 | HTTPS | Secure web |
| 445 | SMB | File sharing (direct) |

**SMB (139/445)** - Most common target for pentesting.

### UDP

| Port | Service |
|------|---------|
| 53 | DNS |
| 67/68 | DHCP |
| 69 | TFTP |
| 161 | SNMP |

## OSI Model

Mnemonic: **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way

| Layer | Name | Examples |
|-------|------|----------|
| 1 | Physical | Cables, Cat6 |
| 2 | Data Link | Switches, MAC addresses |
| 3 | Network | IP addresses, routing |
| 4 | Transport | TCP/UDP |
| 5 | Session | Session management |
| 6 | Presentation | WMV, JPEG, MOV |
| 7 | Application | HTTP, SMTP |

## Subnetting

Most common: `/24` (255.255.255.0)

Example: `172.16.50.0/24`
- Network ID: `172.16.50.0`
- Broadcast: `172.16.50.255`
- Usable hosts: 254 (network and broadcast take 2)

**Calculator:** https://ipaddressguide.com
