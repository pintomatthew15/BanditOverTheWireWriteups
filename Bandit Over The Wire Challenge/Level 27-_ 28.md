Bandit Level 27 → Level 28
Level Goal
There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.


Commands you may need to solve this level
git

Commands Used:
We make a temporary directory and clone the repo using the following command
```
$ git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo.git/
```

We enter the password to the previous level and clone a directory named ```repo```. We cd into the repo directory list its contents and cat a README file. 
```
$ cat README
The password to the next level is: AVanL161y9rsbcJIsFHuw35rjaOM19nR
```

Password:
AVanL161y9rsbcJIsFHuw35rjaOM19nR

