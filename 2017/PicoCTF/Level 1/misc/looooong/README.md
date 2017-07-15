# looooong

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | looooong | Misc | 20 |

### Description
> I heard you have some "delusions of grandeur" about your typing speed. How fast can you go at shell2017.picoctf.com:14319?

## Write-up
Let's connect to that address.  `nc shell2017.picoctf.com 14319` and we see the following result:
```
To prove your skills, you must pass this test.                                                     
Please give me the 'r' character '561' times, followed by a single '2'.                            
To make things interesting, you have 30 seconds.                                                   
Input:
```

Seems like some text manipulation is needed. Let's open Vim.  This solution was dependent on the required character being the same every time which, after another `nc shell2017.picoctf.com 14319`, we learn is not the case.  The hints mention Python so let's see if we can write a quick program.

#### Flag
`HERE_GOES_THE_FLAG`
