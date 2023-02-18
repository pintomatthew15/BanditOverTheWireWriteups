Bandit Level 18 → Level 19
Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

Commands you may need to solve this level
ssh, ls, cat

Commands Used:
In this level, we need to connect using the ssh -t. The -t parameter basically opens a pseudo-tty within the session, with output in the same screen. The ssh session closes when the command completes. This way, you can quickly run a command before the connectivity closes and kicks you out with a “Byebye!”.

```
$ ssh -t bandit18@localhost cat readme
```


Password:
awhqfNnAbc1naukrpqDYcF95h7HoMTrC





