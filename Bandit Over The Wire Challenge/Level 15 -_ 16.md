Bandit Level 15 → Level 16
Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap

Commands Used:
```
$openssl s_client -quiet -connect localhost:30001
...
...
...
<Password from last level>
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

Password:
JQttfApK4SeyHwDlI9SXGR50qclOAil1