# Scripting with Bash

## Ping Sweep Script

### Basic Ping Commands

```bash
# Single ping
ping -c 1 TARGET_IP

# Save to file
ping -c 1 TARGET_IP > ip.txt

# Extract IP from output
cat ip.txt | grep "64 bytes" | cut -d " " -f 4 | tr -d ":"
```

### IP Sweep Script

```bash
#!/bin/bash

if [ "$1" == "" ]
then
    echo "You forgot an IP address!"
    echo "Syntax: ./ipsweep.sh 172.16.50"
else
    for ip in $(seq 1 254); do
        ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" &
    done
fi
```

**Note:** Using `&` runs pings in parallel (faster). Using `;` runs sequentially (slower).

### Usage

```bash
# Make executable
chmod +x ipsweep.sh

# Run and save results
./ipsweep.sh 172.16.50 > ips.txt
```

## Automated Nmap Scanning

```bash
# Scan all discovered hosts
for ip in $(cat ips.txt); do nmap $ip & done

# Full scan
nmap -T4 -A -p- TARGET_IP
```
