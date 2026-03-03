# Kali Linux

## Basics

- `sudo` - Super user do (run as admin). **Be careful when running as super user.**
- `su` - Switch user
- `sudo su` - Switch to root
- `cat` - View, concatenate, create, copy, merge file contents

## Terminal Info

- `[~]` in prompt means `/home/<user>`
- Tab key auto-completes commands and paths
- **Terminal is case sensitive**

### Color Scheme

- Dark Blue - Directory
- Light Blue - Symlink
- Files starting with `.` are hidden (e.g., `.bashrc`)

### Prompt Format

```
(user@host)-[location]
```

## Common Commands

| Command | Description |
|---------|-------------|
| `pwd` | Print working directory |
| `cd` | Change directory (`cd ~` = home, `cd ..` = back) |
| `ls` | List directory contents |
| `ls -la` | List all with details (including hidden) |
| `mkdir` | Create directory |
| `rmdir` | Remove empty directory |
| `rm` | Remove file (`rm -r` for directories) |
| `cp` | Copy files |
| `mv` | Move/rename files |
| `man` | Manual pages (e.g., `man ls`) |
| `echo` | Print to screen |
| `locate` | Find files (run `sudo updatedb` first) |
| `passwd` | Change password |

## Keyboard Shortcuts

- `Ctrl + L` - Clear terminal
- `Ctrl + C` - Cancel/interrupt command
