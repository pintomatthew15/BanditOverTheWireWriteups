Bandit Level 26 → Level 27
Level Goal
Good job getting a shell! Now hurry and grab the password for bandit27!

Commands you may need to solve this level
ls


Commands Used:
```
$ ls

```

We find an executable that uses the setuid function to run with the permissions of bandit27.

Entering the following command we receive the password for then next level
```
$ ./bandit27-do cat /etc/bandit_pass/bandit27

YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
```

Password:
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
