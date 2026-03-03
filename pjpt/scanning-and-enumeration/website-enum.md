# Website Enumeration

Discovering directories, files, and technologies on web servers.

## Directory Brute Forcing

### dirb

```bash
# Basic scan with default wordlist
dirb http://TARGET_IP

# With a specific wordlist
dirb http://TARGET_IP /usr/share/wordlists/dirb/big.txt
```

### ffuf

```bash
# Directory fuzzing
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://TARGET_IP/FUZZ

# Filter by status code
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://TARGET_IP/FUZZ -mc 200,301,302

# Filter out specific response size (remove noise)
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://TARGET_IP/FUZZ -fs 1234

# File extension fuzzing
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://TARGET_IP/FUZZ -e .php,.html,.txt,.bak
```

### gobuster

```bash
# Directory mode
gobuster dir -u http://TARGET_IP -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

# With file extensions
gobuster dir -u http://TARGET_IP -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt
```

## Vulnerability Scanning

### nikto

```bash
# Basic scan
nikto -host http://TARGET_IP

# Specific port
nikto -host TARGET_IP -port 8080

# With SSL
nikto -host https://TARGET_IP
```

Checks for outdated software, misconfigurations, default files, and known vulnerabilities.

## Tips

- Always check `robots.txt` and `sitemap.xml` manually
- View page source for comments, hidden fields, and JS files
- Check for common paths: `/admin`, `/login`, `/backup`, `/config`
- Use Burp Suite spider for more thorough crawling
- Run multiple wordlists if the first doesn't find much
