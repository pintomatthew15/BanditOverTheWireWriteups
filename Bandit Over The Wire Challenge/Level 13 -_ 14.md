Bandit Level 13 → Level 14
Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap

Commands Used
```
$ ssh bandit13@bandit.labs.overthewire.org -p 2220
```

To access the next level, we simply login using the sshkey.private which was provided to us on the home directory using the following command:
```
$ ssh -i sshkey.private bandit14@localhost -p 2220
```

Now that we have authenticated to ```bandit14``` we will print the password in ```/etc/bandit_pass/bandit14``` 
```
$ cat /etc/bandit_pass/bandit14
```

Password:
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
