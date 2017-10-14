# EVENT_NAME YEAR: challenge_name

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Hash101 | Crypto | 50 |

### Description
> Prove your knowledge of hashes and claim a flag as your prize! Connect to the service at shell2017.picoctf.com:46122

## Write-up
First, we have to connect to the service so we enter `nc shell2017.picoctf.com 46122`.  There are four levels of hash manipulation.  We are given the binary number `0110010101100001011100100111010001101000` and need to translate that into an ASCII representation. We get `earth`.  The next level is string to hex, which gives us `6561727468`.  After that is hex to decimal, which gives us `435426587752`.  Next level: 

```
A Hashing Function intakes any data of any size and irreversibly transforms
it to a fixed length number. For example, a simple Hashing Function could be
to add up the sum of all the values of all the bytes in the data and get the remainder
after dividing by 16 (modulus 16)

TO UNLOCK NEXT LEVEL, give me a string that will result in a 2
after being transformed with the mentioned example hashing function
```
We enter `test` which gives us a result of 0.  From there, we can add two more characters to get a result of 2 and advance to the next level.  The final level gives us the following MD5 hash to crack or look up:
`3a663354e45f1dbf9702ffa5dc799c2f`

Using [CrackStation](https://crackstation.net/), we get the string `3l3c7` which gives us the flag.

#### Flag
`a24c028f0a572b9101afd00c86734472`
