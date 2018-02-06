## 0 -> 1
### Level Goal

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
### Solution
`cat readme` -> `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`

---

## 1 -> 2
### Level Goal
The password for the next level is stored in a file called **-** located in the home directory.
### Solution
Bash interprets a dash as stdin so we need to enter `cat ./-`

PW: `CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`

---

## 2 -> 3
### Level Goal
The password for the next level is stored in a file called **spaces in this filename** located in the home directory.
### Solution
Filenames with spaces in them need quotes so we enter `cat "spaces in this filename"`

PW: `UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`

---

## 3 -> 4
### Level Goal
The password for the next level is stored in a hidden file in the **inhere** directory.
### Solution
We don't see anything in the `inhere` directory so we enter `ls -a`, which shows all hidden files.  This shows us the `.hidden` file which we can read the contents of.

PW: `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`

---

## 4 -> 5
### Level Goal
The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.
### Solution
There are many files in the `inhere` directory and we don't want to manually enter `cat` for all of them.  We can enter `cat * */*` to display the outputs of all files and see which one is readable.  This gives us the password.

PW: `koReBOKuIDDepwhWk7jZC0RTdopnAYKh`

---

## 5 -> 6
### Level Goal
The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

### Solution
When we enter the `inhere` directory, we see countless directories and subdirectories.  We can't possibly go through all of these so we need a way to find the right file by given size of 1033 bytes.  We enter `find -size 1033c` and get the following result: `./maybehere07/.file2`  We read this file and get the flag.

PW: `DXjZPULLxYr17uwoI01bNLQbtFemEgo7`

---

## 6 -> 7
### Level Goal
The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

### Solution
All we know is that the password is in a file somewhere on the server.  We do have specific traits about the file though so we go to the root directory and enter `find -user bandit7 -group bandit6 -size 33c`.  This gives us the path `/var/lib/dpkg/info/bandit7.password`.  When we look in that file, we find the password.

PW: `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`

---

## 7 -> 8
### Level Goal
The password for the next level is stored in the file **data.txt** next to the word **millionth**

### Solution
Let's take a look at the data.txt file and see what we find.  There are countless lines in this file, each with a keyword and password.  This is clearly too much to go through manually so we need to use grep.
```bash
$ cat data.txt | grep millionth
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
PW: `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`

---

## 8 -> 9
### Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

### Solution
As usual, let's look at data.txt and see what we find.  It's full of complete gibberish so we need to find the line of text that is unique.  The hints told us to look at the `sort` and `uniq` commands.  Using [TLDR](https://tldr.ostera.io), we look up the syntax for these commands.  We must use the `-u` parameter for `uniq` to display only unique lines.  We enter the following:
```bash
$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
PW: `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`

---

## 9 -> 10
### Level Goal
The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, beginning with several ‘=’ characters.

### Solution
Since data.txt is un-readable, `cat data.txt` does not work.  Even using grep and cat produces no output.  We then try `strings data.txt` and get a readable output so grep should work.
```bash
$ strings data.txt | grep ==
========== theOkM
========== password
========== is
)========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
PW: `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`

---

## 10 -> 11
### Level Goal
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

### Solution
This one was fairly easy.  After looking at the contents of `data.txt`, it is clearly base64 encoded as we were told.  We can confirm this by seeing the double equals sign at the end of the code.  Using the `coreutils` package, we can simply decode this in bash.
```bash
$ cat data.txt | base64 --decode
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
PW: `IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`

---

## 11 -> 12
### Level Goal
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

### Solution
Another easy cryptography problem.  We look in `data.txt` and find our cipher text, which we know has been shifted by 13 positions.  This is a Caesar cipher which we can easily decode [online](http://md5decrypt.net/en/Caesar/).  This gives us the following plaintext:

`the password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`.

PW: `5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`

---

## 12 -> 13
### Level Goal
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

### Solution
This problem was more tedious than anything else.  I had to use multiple decompression techniques including bzip2, gzip, and tar.  After decompressing many times, I finally got the password in a text file.

PW: `8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL`

---

## 13 -> 14
### Level Goal
The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14.** For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note: localhost** is a hostname that refers to the machine you are working on

### Solution
This level requires ssh.  We are provided a private keyfile and to use this to log in instead of a password, we need to use the -i option with ssh.

```bash
$ ssh -i sshkey.private bandit14@localhost
```
We're in.  We can then navigate to the given folder and find the password.
```bash
$ cat ../../etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

PW: `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`

---

## 14 -> 15
### Level Goal
The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

### Solution
This level uses nc (or netcat).  After establishing a connection to localhost on the given port, we can simply enter the previous level's password and receive the password for this level.
```bash
$ nc localhost 30000
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```

PW: `BfMYroe26WYalil77FoDi9qh59eK5xNr`

---

## 15 -> 16
### Level Goal
The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

### Solution
Another relatively simple network connection.  We need to use openSSL with s_client to connect to the given port.  We also need to add the -ign_eof option to allow for input.  We enter `openssl s_client -connect localhost:30001 -ign_eof` and establish connection.  After that, we enter the previous level's password and receive our password.

PW: `cluFn7wTiGryunymYOu4RcffSxQluehd`

---

## 16 -> 17
### Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

### Solution
I liked this one since it finally involved port scanning.  First, we need to find open ports in the given range.
```
$ nmap localhost -p31000-32000
Starting Nmap 7.01 ( https://nmap.org ) at 2018-01-23 16:05 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00043s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
```
We have our ports.  We then use openSSL to connect to each of these, checking which one allows us to enter a password.  We finally find the right connection on port 31790 and receive an RSA private key.

PW: 
```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

---

## 17 -> 18
### Level Goal
There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**.

### Solution
The hardest part about this level was realizing that I had to access the shell from the previous level and then access this level with the RSA key we accessed before.  To do this, we go to the `tmp` folder and create sshkey.private in vim.  We also have to enable permissions for this file using `chmod 600 sshkey.private`.  We then connect to the server using `ssh -i sshkey.private bandit17@localhost`.  We're in.  After this, we have two slightly different files which we can analyze using diff.  After we type `diff passwords.old passwords.new`, we receive the password for this level.

PW: `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` 

---

## 18 -> 19
### Level Goal
The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

### Solution
This one was interesting.  As soon as we attempt to log in with SSH normally, we are instantly kicked out of the server.  We clearly need to modify the ssh command in some way.  After a little googling, I found out that we can use a parameter to ignore the .bashrc.  After typing `ssh bandit18@bandit.labs.overthewire.org -p 2220 "bash --noprofile --norc"`, we enter the password and can easily just read the contents of the readme file.

PW: `IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x`
