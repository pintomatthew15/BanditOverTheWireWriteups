Bandit Level 12 → Level 13
Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

Commands Used:
```
$ mkdir /tmp/matthew123
$ cp data.txt /tmp/matthew123
$ cd /tmp/matthew123
$ ls
data.txt
```

This makes the copy of the file in a temporary directory named ```matthew123```

We must next make a reverse hexdump. ```xxd``` program is used to make a hexdump or to do the reverse. Option ```-r``` converts hexdumps into the binary. 

We use the command
```
xxd -r data.txt > reversed.bin
```

We then use the command ```file``` to determine what type of compressed file ```reversed.bin``` is. We find that it is gzip compressed data. We can use ```zcat``` which is supplied with ```gzip``` to decompress gzip compressed files. 
```
$ file reversed.bin
$ zcat reversed.bin > decompressed
```

Running ```file``` on ```decompressed``` reveals it to be a bzip2 compressed data. ```bzcat``` program is supplied with ```bzip2``` and is used to decompress bzip2 compressed files.
```
file decompresssed
bzcat decompressed > decompressed2

```

```decompressed2``` is gzip compressed file so we use ```zcat``` to decompress it into ```decompressed3```.  
```
$ file decompressed2
$ zcat decompressed2 > decompressed 3
$ file decompressed3
```

```decompressed3``` is a POSIX tar archive.

```tar``` is a program used for archiving file and option ```-x``` is used to extract an archive, ```-f``` is used to specify name of the tar archive and ```-v``` is used for more detailed listings.
```
$ tar -xvf decompressed3 
```

This command outputs the file ```data5.bin```, which is again another tar archive.  we use ```tar``` again which outputs ```data6.bin```. ```data6.bin``` is a bzip2 compressed file so we will use ```bzcat``` to decompress the program to ```decompressed7```. 
```
$ tar -xvf data5.bin
$ bzcat data6.bin > compressed7
```


```compressed7``` is a tar archive and we use the ```tar``` program to ouput ```data8.bin```. 
```
$ file compressed7
$ tar -xvf compressed7
data8.bin
```


```data8.bin``` is a gzip compressed file so we will use ```zcat``` to make ```compressed9```
```
$ file data8.bin
$ zcat data8.bin > compressed9
```

We run ```file``` on compressed9 and finally find a file that contains ASCII text
```
$ file compressed9
compressed9: ASCII text
```

Password:
wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw