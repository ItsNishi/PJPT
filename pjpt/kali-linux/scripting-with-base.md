# Scripting with Base

ifconfig



ping #address -c 1 -- sends 1 packet

&#x20;ping #address -c 1 > ip.txt -- saves to ping to text file

cat ip.txt | grep "64 bytes" - extracts 1 line of data and pints to cli

cat ip.txt | grep "64 bytes" | cut -d " " -f 4 -- cuts the data and only prints the ip. the delimiter uses " " to jump between the characters and finds the ip in the text file

cat ip.txt | grep "64 bytes" | cut -d " " -f 4 L tr -d ":" --- used translate to get rid of the colon at the end of the ip address



`pingsweep -`

`#!/bin/bash`

`if [ "$1" == "" ]`&#x20;

`then`&#x20;

`echo "You forgot an IP address!"`&#x20;

`echo "Syntax: ./ipsweep.sh 192.168.1"`

`else`&#x20;

`for ip in seq 1 254; do`&#x20;

`ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" & ---- can use ; instead of &, but will run slower.`

`done`&#x20;

`fi`



can be stored in file

./ipsweep.sh 192.168.1 > ips.txt



nmap -T4 -A -p -- scan all and scan ports

for ip in $(cat ips.txt); do nmap $ip; & done
