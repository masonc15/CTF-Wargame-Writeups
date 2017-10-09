## 0 -> 1
### Level Goal

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
### Solution
`cat readme` -> `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`

---

## 1 -> 2
### Level Goal
The password for the next level is stored in a file called - located in the home directory.
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


---

## 5 -> 6
### Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

### Solution

