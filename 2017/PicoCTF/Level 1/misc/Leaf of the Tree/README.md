# PicoCTF 2017: Leaf of the Tree

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Leaf of the Tree | Misc | 20 |

### Description
> We found this annoyingly named directory tree starting at `/problems/8ca1c927e4aedb1db7961d774fa56bcd`. It would be pretty lame to type out all of those directory names but maybe there is something in there worth finding? And maybe we dont need to type out all those names...? Follow the trunk, using cat and ls!

## Write-up
This seems to be a simple file location problem.  However, the file is hidden within many long and hard-to-type directory names.  We find the given `/problems/8ca1c927e4aedb1db7961d774fa56bcd` directory very easily.  I know what `cat` and `ls` do and I figured that some parameters could be added to these commands to easily find the flag.  A quick `man ls` gave us `ls -R`, which seems to be a recursive directory search.  

This gives us the following:
```
./trunk/trunk9b95/trunkb610/trunkcd2e/trunk2498/trunk24e1/trunk1d04/trunk52c5:                     
branch6b9b  flag
```

`cat flag` gives us the flag.

#### Flag
`d0bc754c90a5514b4d10d2f038eba8df`
