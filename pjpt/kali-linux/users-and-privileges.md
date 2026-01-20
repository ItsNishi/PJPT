# Users and Privileges

## File Permissions

Format: `drwxrwxrwx`

First character:
- `d` - Directory
- `l` - Symbolic link
- `-` - Regular file

Permission groups (rwx):
1. **Owner** - File owner permissions
2. **Group** - Group membership permissions
3. **Other** - All other users

Permission meanings:
- `r` - Read
- `w` - Write
- `x` - Execute
- `-` - Permission not granted

Examples:
- `rwx` - Read, write, execute
- `rw-` - Read, write only
- `r-x` - Read, execute only

## Changing Permissions

```bash
# Symbolic mode
chmod +rwx file.txt        # Add all permissions
chmod +x script.sh         # Add execute

# Numeric mode
chmod 777 file.txt         # Full permissions for all
chmod 644 file.txt         # Owner rw, others read only
chmod 400 keyfile.pem      # Owner read only (SSH keys)
```

**SSH key files require:** 644 or 400

## Important System Files

```bash
# User accounts
/etc/passwd

# Password hashes (requires root)
/etc/shadow

# Sudo privileges
/etc/sudoers
```

## Checking Privileges

```bash
# Check who has sudo access
grep 'sudo' /etc/group
```
