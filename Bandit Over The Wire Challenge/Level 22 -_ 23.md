Bandit Level 22 → Level 23
Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

Commands:
Much like the last level, we view the ```/etc/cron.d``` folder and cat the cronjob for the current level
```
$ cd /etc/cron.d
$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```

We change directories to ```/usr/bin``` and cat ```cronjob_bandit23.sh```
```
$ cd /usr/bin
$ cat cronjob_bandit23.sh

#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

The shell code basically creates an md5 hash of the string “echo I am user bandit22 | md5sum | cut –d ‘ ‘ –f 1”

Since we need the password of bandit23, let’s manually run the hash and use its hash as the directory name. The password might be there, provided that someone with the bandit23 credentials has already ran this script (they probably have).

```
$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```

Password:
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G