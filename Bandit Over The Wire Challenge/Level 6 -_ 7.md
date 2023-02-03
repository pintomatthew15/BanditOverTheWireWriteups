Bandit Level 6 → Level 7
Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size
Commands you may need to solve this level
ls , cd , cat , file , du , find , grep

Commands Used:
```
$ find / -size 033c -user bandit7 -group bandit6

$ cd /var/lib/dpkg/info
$ cat bandit7.password
```

Password:
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

