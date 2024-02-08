# Navigating the File System

Sudo - Super user do - run as admin \***BECARE WHEN RUNNING AS SUPER USER**\*

cat - allowing users to view, concatenate, create, copy, merge, and manipulate file contents

su - switch user

sudo su - switch to root

**\[\~**] in cli - means /home/(user)

Can auto-complete in the terminal if you hit  tab

**Terminal is Case sensitive**



Color scheme to differentiate between different items

Dark Blue - Folder

Lighter Blue - File



anything with a  (**.**) is a hidden IE: .java&#x20;



&#x20;**Terminal Header Breakdown**

(kali@kali)-\[\~] == (user@host - location)



**COMMANDS**

* pwd - Print Working Directory
* cd - change directory
  * can **cd \~** to go home
* cd .. - goes back a directory
  * can only tab and autocomplete if in the same directory IE: **Downloads,** while in the home folder directory
  * providing full path, you can go anywhere IE: **/etc/**
* ls - list items in the directory you are in
  * Can list files not in the current directory using **ls /etc/**
  * **ls -la** (long all) - can think of list all
  * \-l use long listing format aka more details
  * \-a or --all - do not ingnore entries starting with .
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





**SHORT CUTS**

* CTRL + L - Clear terminal





