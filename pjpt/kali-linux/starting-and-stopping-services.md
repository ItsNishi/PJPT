# Starting and Stopping Services

## Service Management

```bash
# Start/stop Apache
sudo service apache2 start
sudo service apache2 stop

# Enable SSH on boot
sudo systemctl enable ssh

# Start SSH now
sudo systemctl start ssh
```

## Quick Web Server

Python's built-in HTTP server:

```bash
python3 -m http.server 80
```

- `-m` calls the http.server module
- `80` is the port (needs sudo for ports < 1024)
- `Ctrl + C` to stop
