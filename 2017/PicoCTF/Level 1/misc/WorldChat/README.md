# WorldChat

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | WorldChat | Misc | 30 |

### Description
> We think someone is trying to transmit a flag over WorldChat. Unfortunately, there are so many other people talking that we can't really keep track of what is going on! Go see if you can find the messenger at shell2017.picoctf.com:14747. Remember to use Ctrl-C to cut the connection if it overwhelms you!

## Write-up
This was possibly my favorite problem so far although I have just started.  First, we `nc shell2017.picoctf.com 14747` and see what happens.  We're immediately overwhelmed with many chat messages and timestamps spouting random nonsense.  Mostly random.  After pressing `Ctrl-C` to cut off the connection, we go back over and analyze the chat.  There is one line that stands out in particular: 

`18:25:35 flagperson: this is part 6/8 of the flag - 79a4 `.

In the midst of all this chat, the flag is being transmitted in multiple parts by the user flagperson. In the Leaf of the Forest problem, I learned that the grep command would be useful in this situation so we enter `nc shell2017.picoctf.com 14747 | grep flagperson`.  At first, there is no output but after a minute or two, we see the following.
```
18:26:58 flagperson: this is part 1/8 of the flag - ab4b
18:27:07 flagperson: this is part 2/8 of the flag - 181f
18:27:08 flagperson: this is part 3/8 of the flag - 3bc9
18:27:08 flagperson: this is part 4/8 of the flag - 2758
18:27:10 flagperson: this is part 5/8 of the flag - 9e0d
18:27:12 flagperson: this is part 6/8 of the flag - 79a4
18:27:20 flagperson: this is part 7/8 of the flag - 845a
18:27:21 flagperson: this is part 8/8 of the flag - 3ace
```
We combine these and get our flag.

#### Flag
`ab4b181f3bc927589e0d79a4845a3ace`
