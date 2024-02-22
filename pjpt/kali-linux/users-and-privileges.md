# Users and Privileges

![](<../../.gitbook/assets/image (1) (1).png>)

This Screenshot shows the permissions of the file in the directory

The first letter indicates what the item is listed

**d** = Directory/Folder

**l** = Link also shows as lighter blue

RWX = Read, Write, Execute

If missing letter means it can not do one of the followings

\-WX = Write, Execute

RW- = Read, Write

R-X = Read, Execute

The First group of permissions(RWX) is the owner of the file

The second group of permissions(RWX) is group membership or is a part of the owner group

The Third group of permissions(RWX) is other users



using ls -la /tmp&#x20;

the Temp folder has Read, Write, Execute&#x20;

Don't have to worry about permissions as much



creating a file and changing the permissions

echo "hello" > hello.txt #prints makes text file with hello in it

chmod = change mode | used to alter permissions

chmod +rwx hello.txt = changes the permissions of the file to read, write, execute for the user

chmod 777 - changes all permission to read, write, execute

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

SSH PEM file require - 644 or 400

How to add a user

**Important Locations**

**User ID location**

```
/etc/passwd
```

Shadow file - Where password hashes are

```
/etc/shadow
```

Sudoers - people has admin

```
/etc/sudoers
```

grep - used to pull strings or elements out of files

grep 'sudo' /etc/group - checks who has admin privileges&#x20;
