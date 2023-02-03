Bandit Level 9 → Level 10
Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

**Solution**
We see that data.txt is a binary file and not a normal ASCII text file. By running 
```
$ file data.txt
data.txt: data

$ strings data.txt | grep =
```

Password:
G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s



