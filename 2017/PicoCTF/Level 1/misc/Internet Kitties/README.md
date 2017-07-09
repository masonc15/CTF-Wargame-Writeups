# Internet Kitties

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| DEF CON CTF Quals | Internet Kitties | misc | 10 |

### Description
> I was told there was something at IP shell2017.picoctf.com with port 42354. How do I get there? Do I need a ship for the port?

## Write-up

This is an intro CTF so these first problems shouldn't be too hard. Looks like I just need to connect to port 42354 on the given address.  At first, I thought an SSH connection was required so I tried `ssh shell2017.picoctf.com:42354`.  No luck.  The hint mentioned using Netcat which I haven't used before.  A quick `man nc` gives us the syntax and entering in the correct command gives us the flag.

```
shadronix@shell-web:~$ nc shell2017.picoctf.com 42354                                              
Yay! You made it!                                                                                  
Take a flag!                                                                                       
74d4fd0abc13a085d6d60489db227dfd 
```
