# Sockets

A socket uniquely identifies the endpoint of a communication link between two application ports.

```
#!/bin/python3
import socket

HOST = '127.0.0.1'

PORT = 1337

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) #af_inet is ipv4 sock_stream is a port
s.connect((HOST,PORT))

```

```
#creating port for listening on Kali Linux
nc -nvlp 1337 
```
