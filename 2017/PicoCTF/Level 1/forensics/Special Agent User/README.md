# Special Agent User

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | Special Agent User | Forensics | 50 |

### Description
> We can get into the Administrator's computer with a browser exploit. But first, we need to figure out what browser they're using. Perhaps this information is located in a network packet capture we took: data.pcap. Enter the browser and version as "BrowserName BrowserVersion". NOTE: We're just looking for up to 3 levels of subversions for the browser version (ie. Version 1.2.3 for Version 1.2.3.4) and ignore any 0th subversions (ie. 1.2 for 1.2.0)

## Write-up
Another packet analysis problem.  We start up [PacketTotal](https://packettotal.com) again and poke around.  We only need to figure out what browser the user is using which luckily, is listed in the interface as User Agent.  In the HTTP connections, there are many wget agents but only one that is listed as `Mozilla/5.0 (X11 Linux x86_64) AppleWebKit/537.36 (KHTML like Gecko) Chrome/34.0.1847.137 Safari/4E423F`.  We can enter this into [UserAgentString.com](useragentstring.com) to see the detailed browser information.  The Chrome version is what we're looking for so we can extrapolate the flag from that data.

#### Flag
`Chrome 34.0.1847`
