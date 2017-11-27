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

---

## 10 -> 11
### Level Goal
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

### Solution

---

## 11 -> 12
### Level Goal
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

### Solution

---

## 12 -> 13
### Level Goal
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

### Solution

---

## 13 -> 14
### Level Goal
The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14.** For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note: localhost** is a hostname that refers to the machine you are working on

### Solution

