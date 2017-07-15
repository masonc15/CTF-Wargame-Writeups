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
```Python

def speedType(character, numRepeated, addChar):
  
  for x in range(0, numRepeated):
    print (character, end="")
  
  print (addChar)
  
speedType('d', 600, '5')
```
I'm sure it's not the most elegant code, but it'll do.  We connect again and quickly enter the requirements into the speedType function.  After getting our string, we copy that into the shell and receive our flag.  

#### Flag
`with_some_recognition_and_training_delusions_become_glimpses_7827f460d98d8c7e3ba0dfb12656ee06`
