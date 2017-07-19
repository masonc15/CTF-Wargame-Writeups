# computeRSA

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | computeRSA | Crypto | 50 |

### Description
> RSA encryption/decryption is based on a formula that anyone can find and use, as long as they know the values to plug in. Given the encrypted number 150815, d = 1941, and N = 435979, what is the decrypted number?

## Write-up
Another simple crypto problem.  While we could do the actual math, CTFs are about speed and efficiency, at least in my experience.  We find an RSA decryptor [here](https://www.cs.drexel.edu/~introcs/Fa11/notes/10.1_Cryptography/RSA_Express_EncryptDecrypt.html) that allows us to plug in the given variables.  This gives us the decrypted number which is our flag.

#### Flag
`133337`
