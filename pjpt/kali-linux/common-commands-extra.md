# Common Commands - Extra

This is used to show all commands for Linux. Not a main section in the course

* cat - allowing users to view, concatenate, create, copy, merge, and manipulate file contents
* Sudo - Super user do - run as admin \***BECARE WHEN RUNNING AS SUPER USER**\*
* su - switch user
* pwd - Print Working Directory
* cd - change directory
  * cd.. goes back a directory
* ls - list items in the directory you are in
* **mkdir** - to make a folder/directory
* **rmdir** - to delete a folder/directory
* man -- means manual -- Will pull up manual for commands like IE: **man ls** will provide information about the ls command.
* echo - prints to the screen
  * echo 'Hi!' > test.txt -- prints hi into the test text files
* cp - copy
  * cp test.txt downloads -- will copy file into downloads
* rm - remove file
  * can remove while not in directory IE: rm Downloads/test.txt
* mv - move file
* locate - will find file
  * locate test.txt will show all the files named test.txt
  * sudo updatedb -- updates the index/database so you can find files that are new and not indexed
* passwd - change password for user
* chmod - change mode | used to alter permissions
* grep - used to pull strings or elements out of files
* ip a - lists all network adapters/network information, may not be on old machine- new way
* ip n - what ip address is associated with what mac address
* arp -a - address resolution protocol same as **ip n**
* ifconfig - only shows hardwire connections as **ip a,** but may need sudo
* iwconfig - shows wireless connections

ping #address -c 1 -- sends 1 packet

&#x20;ping #address -c 1 > ip.txt -- saves to ping to text file

cat ip.txt | grep "64 bytes" - extracts 1 line of data and pints to cli

cat ip.txt | grep "64 bytes" | cut -d " " -f 4 -- cuts the data and only prints the ip. the delimiter uses " " to jump between the characters and finds the ip in the text file

