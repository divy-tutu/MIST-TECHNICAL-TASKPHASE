## Split-piping stderr and stdout
- to split stderr and stdout we cant use tee so we have to use > in a specific way
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{YS5esh3CckoOYr8vF9cDp9_MozU.dFDNwYDLyATO0czW}
hacker@piping~split-piping-stderr-and-stdout:~$
```
