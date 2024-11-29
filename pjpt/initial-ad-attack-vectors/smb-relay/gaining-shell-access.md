# Gaining Shell Access

gaining shell access Metasploit -- is noisy&#x20;



use exploit/windows/smb/psexec



smbdomain - server name of the domain

smbpass - password for a specific user / could use password hash

smb user - user to authenticate





psexec.py use for less noise

psexec.py domain/username:'pass' @ip address --- can use password hash also



make sure the firewall is disabled to preform this attack.



<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Target 2 is best but can choose between 0-2. 3 and 4 don't work as well



msf6 background - lets you execute more commands or exploits while holding the previous shell open



you could basically create a command and control if you want having multiple shells/exploits running in the background



sessions brings up the sessions that are in the background and can select them with the correlating ID



<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

if psexec.py is not working or using anti-virus try wmiexec.py or smbexec.py -- depends on the machine



