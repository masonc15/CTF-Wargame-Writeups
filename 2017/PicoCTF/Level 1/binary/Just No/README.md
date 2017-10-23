# Just No

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Just No | Binary Exploitation | 40 |

### Description
> A program at /problems/ec9da1496f80c8248197ba564097cebb has access to a flag but refuses to share it. Can you convince it otherwise?

## Write-up
This was a difficult one.  First, we find a `justno` executable and `justno.c` at the given directory.  Inside the .c file, we find
```C
FILE* authf = fopen("../../problems/7e8b456c98db60be9a33339ab4509fca/auth","r")
```
The solution clearly involves relative paths.  We can go to our home directory and enter:

```
$ mkdir problems
$ mkdir 7e8b456c98db60be9a33339ab4509fca
$ cd problems/7e8b456c98db60be9a33339ab4509fca
```
Now, we can create an auth file using vim that says yes or anything other than "no".  After doing this, we enter:

```
$ /problems/7e8b456c98db60be9a33339ab4509fca/justno
$ Oh. Well the auth file doesn't say no anymore so... Here's the flag: e4cec8fdf76a931b03ad7ef026103d43
```

#### Flag
`e4cec8fdf76a931b03ad7ef026103d43`
