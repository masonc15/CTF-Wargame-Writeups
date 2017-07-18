# Leaf of the Forest

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Leaf of the Forest | Misc | 30 |

### Description
> We found an even bigger directory tree hiding a flag starting at /problems/b8c0c83a9aa6d7c4963d1bb09b9a33d0. It would be impossible to find the file named flag manually...

## Write-up
As you can tell by the name, this problem is similar to Leaf of the Tree but slightly harder.  In this case, doing a recursive directory listing would produce too many results to go through manually.  As suggested by the description, we need to use a Linux command to find the flag.  I had to do some research and after using `grep` unsuccessfully, I stumbled upon the `find` command.  After reading the [manpage](https://linux.die.net/man/1/find), we navigate to `/problems/b8c0c83a9aa6d7c4963d1bb09b9a33d0/forest` and type the command `find -iname '*flag*'`.  The `-iname` parameter allows us to enter the "flag" string to search for, case insensitive.         

This produces the output `./forest/tree4ae8da/trunk4c10/trunk82f2/trunk8c81/trunk541d/trunk1810/trunk2bce/trunk44a6/branch813d/flag`.  After navigating to that folder, we `cat flag` and receive the hash.                                                              

#### Flag
`f5a1555fd53f554bc846940b71e9f5e7`
