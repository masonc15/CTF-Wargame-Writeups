# What is Web

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | What is Web | Web | 20 |

### Description
> Someone told me that [some guy](https://en.wikipedia.org/wiki/Tim_Berners-Lee) came up with the "World Wide Web", using "HTML" and "stuff". Can you help me figure out what that is? [Website.](http://shell2017.picoctf.com:58191/)

## Write-up
This one was a bit tricky.  We were given another address like the previous problems in the Misc category so my first instinct was to `nc shell2017.picoctf.com 58191`.  This produced no output which, on second thought, makes sense because it's an HTML file.  When I clicked on the link in Chrome, I received an error so it was clear everything would be performed in the shell.

I had played around with the URL command-line data transfer tool [wget](https://www.gnu.org/software/wget/) before so I thought that would be my next option.  We enter `wget http://shell2017.picoctf.com:58191/` and receive the raw HTML of the site.  This provides us with the following comment:
```html
<!-- The first part of the flag (there are 3 parts) is 4eabea7c5b1 -->
```
A good start.  There are some other promising links in the HTML like `hacker.css` and `script.js` so we need to access those next. After browsing the wget manpage, we find the -p parameter which downloads all the files that are necessary to display a given HTML page.  We enter `wget -O downloadedtext.txt  'http://shell2017.picoctf.com:58191/' -p` and then `cat downloadedtext.txt` to see the output.  This output is extremely long and unreadable so a quick `grep "flag" downloadedtext.txt` should help.  This outputs the following:
```
<!-- The first part of the flag (there are 3 parts) is 4eabea7c5b1 -->
The second part of the flag is e8e0c84cc61 
.glyphicon-flag:before{content:"\e034"}
 * The final part of the flag is 2a79d2dc833
```
In addition to the part from before, there are two more parts of our flag.  Success.
#### Flag
`4eabea7c5b1e8e0c84cc612a79d2dc833`
