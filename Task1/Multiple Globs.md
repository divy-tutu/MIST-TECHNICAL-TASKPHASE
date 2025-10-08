Globbing allows us to basically put placeholders for finding files, like a fill in the blank. *ph would mean any word ending with ph.
<br>
<br>
While * is like a fill in the blank, ? is like fill in the character
```
divyesh@UbuntuLinux:~$ ssh-keygen -f key -N ''
Generating public/private ed25519 key pair.
Your identification has been saved in key
Your public key has been saved in key.pub
The key fingerprint is:
SHA256:7nAdQYUTLyzuCbj6ODBkgkxEOfEAr0YylDEFFBQOgHw divyesh@UbuntuLinux
The key's randomart image is:
+--[ED25519 256]--+
|&#X.      o+.    |
|=B+E     oo.     |
|*o+.    . +..    |
|=*   . . . o     |
|=.  . . S .      |
|+    . + o .     |
| o  . . = .      |
|  .o   +         |
|  oo.   .        |
+----[SHA256]-----+
divyesh@UbuntuLinux:~$ cat key.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILHnAhF0Ld1Y9i2GenU/IFq+WMuzF/aKUR0rNPCIz3VA divyesh@UbuntuLinux
divyesh@UbuntuLinux:~$ ssh -i key hacker@dojo.pwn.college
No active challenge session; start a challenge!
Connection to dojo.pwn.college closed.
divyesh@UbuntuLinux:~$  ssh -i key hacker@dojo.pwn.college
Command ' ssh' not found, did you mean:
  command 'mssh' from deb mssh (2.2-5.1)
  command 'ssh' from deb openssh-client (1:9.6p1-3ubuntu13.14)
  command 'zssh' from deb zssh (1.5c.debian.1-9)
  command 'sssh' from deb guile-ssh (0.16.4-1)
  command 'cssh' from deb clusterssh (4.16-4)
  command 'bssh' from deb avahi-ui-utils (0.8-13ubuntu2)
Try: sudo apt install <deb name>
divyesh@UbuntuLinux:~$  ssh -i key hacker@dojo.pwn.college
Command ' ssh' not found, did you mean:
  command 'zssh' from deb zssh (1.5c.debian.1-9)
  command 'sssh' from deb guile-ssh (0.16.4-1)
  command 'mssh' from deb mssh (2.2-5.1)
  command 'cssh' from deb clusterssh (4.16-4)
  command 'ssh' from deb openssh-client (1:9.6p1-3ubuntu13.14)
  command 'bssh' from deb avahi-ui-utils (0.8-13ubuntu2)
Try: sudo apt install <deb name>
divyesh@UbuntuLinux:~$  ssh -i key hacker@dojo.pwn.college
Command ' ssh' not found, did you mean:
  command 'sssh' from deb guile-ssh (0.16.4-1)
  command 'bssh' from deb avahi-ui-utils (0.8-13ubuntu2)
  command 'cssh' from deb clusterssh (4.16-4)
  command 'ssh' from deb openssh-client (1:9.6p1-3ubuntu13.14)
  command 'zssh' from deb zssh (1.5c.debian.1-9)
  command 'mssh' from deb mssh (2.2-5.1)
Try: sudo apt install <deb name>
divyesh@UbuntuLinux:~$  ssh -i key hacker@dojo.pwn.college
Command ' ssh' not found, did you mean:
  command 'mssh' from deb mssh (2.2-5.1)
  command 'cssh' from deb clusterssh (4.16-4)
  command 'bssh' from deb avahi-ui-utils (0.8-13ubuntu2)
  command 'sssh' from deb guile-ssh (0.16.4-1)
  command 'zssh' from deb zssh (1.5c.debian.1-9)
  command 'ssh' from deb openssh-client (1:9.6p1-3ubuntu13.14)
Try: sudo apt install <deb name>
divyesh@UbuntuLinux:~$ ssh -i key hacker@dojo.pwn.college
                                                                                Connected!
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /*p*
bash: /opt: Is a directory
hacker@globbing~multiple-globs:/challenge/files$ cat /*p*
cat: /opt: Is a directory
cat: /proc: Is a directory
cat: /tmp: Is a directory
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{M54Mwo2ZFpkhI4iEpLSwgSRmSxW.QXycTO2EDLyATO0czW}
hacker@globbing~multiple-globs:/challenge/files$ 
```

initially i thought *P* is the run command, but had to pass it as arguement
