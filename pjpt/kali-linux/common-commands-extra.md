# Common Commands - Extra

Additional Linux commands reference.

## File Operations

| Command | Description |
|---------|-------------|
| `cat` | View/concatenate file contents |
| `sudo` | Run as superuser |
| `su` | Switch user |
| `pwd` | Print working directory |
| `cd` | Change directory |
| `ls` | List directory contents |
| `mkdir` | Create directory |
| `rmdir` | Remove empty directory |
| `rm` | Remove file |
| `cp` | Copy file |
| `mv` | Move/rename file |
| `locate` | Find file (use `sudo updatedb` first) |
| `man` | Manual pages |
| `echo` | Print to screen |
| `passwd` | Change password |
| `chmod` | Change file permissions |
| `grep` | Search text patterns |

## Network Commands

| Command | Description |
|---------|-------------|
| `ip a` | List all network interfaces (modern) |
| `ip n` | Show ARP table (IP to MAC) |
| `arp -a` | Show ARP table (legacy) |
| `ifconfig` | Network config (legacy, needs sudo) |
| `iwconfig` | Wireless config |

## Ping and Text Processing

```bash
# Send single ping
ping -c 1 TARGET_IP

# Save output to file
ping -c 1 TARGET_IP > ip.txt

# Extract specific line
cat ip.txt | grep "64 bytes"

# Extract just the IP (4th field, space delimiter)
cat ip.txt | grep "64 bytes" | cut -d " " -f 4

# Remove trailing colon
cat ip.txt | grep "64 bytes" | cut -d " " -f 4 | tr -d ":"
```
