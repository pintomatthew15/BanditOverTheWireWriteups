Bandit Level 11 → Level 12
Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd


We know that the characters being rotated by 13 positions translates to ROT which we can decode using this command:

```
cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
```

This is the case sensitive version of the ```tr``` command

Password:
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
