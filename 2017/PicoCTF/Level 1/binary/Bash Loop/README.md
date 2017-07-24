# Bash Loop

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Bash Loop | Binary Exploitation | 40 |

### Description
> We found a program that is hiding a flag but requires you to guess the number it is thinking of. Chances are Linux has an easy way to try all the numbers... Go to /problems/e3f1970eb419b3aa32788a43ec91ef08 and try it out!

## Write-up
This problem was my first real dive into bash as a scripting language.  First, we navigate to the provided directory and find a `bashloop` executable.  We run this and see the following output:

`What number am I thinking of? It is between 0 and 4096`

It seems like it wants a guess.  We enter `./bashloop 5`, just as an example.  
`Nope. Pick another number between 0 and 4096`

Obviously, we aren't going to sit here and try every number so there must be a way to automate this process.  After some research, I found that I could make a for loop in bash to loop through every number.  We come up with the following script:

```bash
for value in {0..4096}
do
  ./bashloop $value
done
```
After running this, our screen is flooded with failed responses.  We need some way to filter out the incorrect numbers.  `grep` should do the trick.  Our edited script is:

```bash
for value in {0..4096}
do
  ./bashloop $value | grep "flag"
done
```

This gets us the flag.

#### Flag
`9960332950d7db392f97f29dee04f4ee`
