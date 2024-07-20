# Scanning & Enumeration

```
sudo netdiscover -r 192.168.1.0/24 -- scanning an ip range
```

```
nmap -sS - no longer stealthy - does 3 way handshake, but stops after synack
SYN SYNACK RST - never made connection
```

```
nmap -T4 -p- -A ip
```

\-T = speed function 1 slowest - 5 fastest, standard is 4. slower is better for detection. depends on application

\-p- = scan all ports

leave off -p = scans top 1000 ports

\-p 80,443,53 = can scan for specific ports

\-A = everything = version, OS,

\--help - help command

\-sn = ping scan - disables port scan - use a ping sweep

\-pn = treat all hosts as online&#x20;

\-sS/sT/sA/sW/sM - TCP SYN(Stealth Scan)/Connect()/ACK/Window/Maimon scans

\-sU = UDP Scan - take forever to scan do top 1000 -p

\-sV Probe ioen ports to determine service/version info

\-O = enables OS detection

\-sC = Script scanning

\-p = port

\-A = OS detection,version detection,script scanning, traceroute

faster to -p- than -A

could script -a after -p- finished

