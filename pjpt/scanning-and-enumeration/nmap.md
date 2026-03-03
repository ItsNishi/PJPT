# Scanning and Enumeration

## Network Discovery

```bash
sudo netdiscover -r 172.16.50.0/24
```

## Nmap Scanning

### Basic Scans

```bash
# SYN scan (stealth-ish) - sends SYN, receives SYN-ACK, sends RST
nmap -sS TARGET_IP

# Full scan with version detection and scripts
nmap -T4 -p- -A TARGET_IP
```

### Common Flags

| Flag | Description |
|------|-------------|
| `-T4` | Speed (1=slowest, 5=fastest). 4 is standard. |
| `-p-` | Scan all 65535 ports |
| `-p 80,443` | Scan specific ports |
| `-A` | Aggressive (OS, version, scripts, traceroute) |
| `-sn` | Ping scan only (no port scan) |
| `-Pn` | Skip host discovery (treat all as online) |
| `-sV` | Version detection |
| `-O` | OS detection |
| `-sC` | Default scripts |
| `--help` | Show all options |

### Scan Types

| Flag | Type |
|------|------|
| `-sS` | SYN scan (stealth) |
| `-sT` | TCP connect scan |
| `-sA` | ACK scan |
| `-sU` | UDP scan (slow) |
| `-sW` | Window scan |

### Strategy

1. Fast port discovery first: `nmap -p- TARGET_IP`
2. Then detailed scan on open ports: `nmap -A -p PORTS TARGET_IP`
