# Digital Camouflage

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Digital Camouflage | Forensics | 50 |

### Description
> We need to gain access to some routers. Let's try and see if we can find the password in the captured network data: data.pcap.

## Write-up
I have played around with Wireshark before but really haven't done much packet analysis so this provided good experience.  First, I did not have access to Wireshark so I opened an [online packet analyzer](https://packettotal.com) to look at the provided file data.pcap.  I looked around a little bit but did not know immediately what to do.  I saw a "Transferred Files" tab and thought that looked promising.  
![PacketTotal](http://i.imgur.com/k11rKGU.png)

Sure enough, there's one transferred file which has a mime type of text/plain, not text/html.  Let's download this file and see what we get.  We see the following string in the file: `userid=randled&pswrd=OFBGRW8wdHRIUQ%3D%3D`.  Seems to be what we're looking for.  However, the password is encoded in Base64.  A quick decode and we get our flag.

#### Flag
`8PFEo0ttHQ`
