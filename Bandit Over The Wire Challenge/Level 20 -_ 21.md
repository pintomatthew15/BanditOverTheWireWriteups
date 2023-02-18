Bandit Level 20 → Level 21
Level Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

Commands Used:
In this level, basically we need to setup a listener service to listen on any port, and then use the binary submit this level’s password to it. If It is correct, it will provide the password to the next level.

We first check for which ports are open
```
$ nmap localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2023-02-08 22:19 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00013s latency).
Not shown: 993 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1234/tcp  open  hotline
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
8000/tcp  open  http-alt
30000/tcp open  ndmps

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds

```

We will now setup our own listener which will echo the current level password when any clients connect
```
$ echo VxCazJaVykI6W36BkBU0mJTCM8rR95XT
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
$ echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -l -p 60000

```

We then open another terminal window and attempt to connect to the service running on port ```60000``` using the SetUID binary.

Client Screen
```
$ ./suconnect 60000
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
```

Server Screen
```
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```

Password:
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq