# Website Enum

dirb http://ipaddress - finding all the directories from webhost



ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://IPADDRESS/FUZZ - looks one thread deep



nikto -host ipaddress:80
