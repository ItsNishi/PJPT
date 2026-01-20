# Navigating the File System

## Directory Navigation

```bash
pwd                    # Print current directory
cd /path/to/dir        # Change to specific directory
cd ~                   # Go to home directory
cd ..                  # Go up one level
cd -                   # Go to previous directory
```

## Listing Files

```bash
ls                     # List files
ls -l                  # Long format (details)
ls -a                  # Show hidden files
ls -la                 # Both (most useful)
ls /etc/               # List specific directory
```

Flags:
- `-l` - Long listing format (permissions, size, date)
- `-a` - Show all (including hidden files starting with `.`)

## File Operations

```bash
mkdir newdir           # Create directory
rmdir emptydir         # Remove empty directory
rm file.txt            # Remove file
rm -r directory/       # Remove directory and contents
cp source dest         # Copy file
mv source dest         # Move or rename
```

## Finding Files

```bash
locate filename        # Fast search (uses database)
sudo updatedb          # Update locate database
find / -name "file"    # Real-time search
```

## Getting Help

```bash
man command            # Manual page
command --help         # Quick help
```
