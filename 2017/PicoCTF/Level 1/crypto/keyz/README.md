# keyz

## Challenge details
| Event | Challenge | Category | Points |
|:------|:----------|:---------|-------:|
| PicoCTF 2017 | keyz | crypto | 20 |

### Description
> While webshells are nice, it'd be nice to be able to login directly. To do so, please add your own public key to ~/.ssh/authorized_keys, using the webshell. Make sure to copy it correctly! The key is in the ssh banner, displayed when you login remotely with ssh, to shell2017.picoctf.com

## Write-up
This flag seems pretty straightforward.  We just need to generate an SSH key and copy it to `~/.ssh/authorized_keys`.  I mainly followed this [guide](https://confluence.atlassian.com/bitbucketserver/creating-ssh-keys-776639788.html).  We enter the command `ssh-keygen -t rsa`, follow the prompts, and we should be good.  Finally, we need to make sure it's in the right directory so we enter `cp id_rsa.pub ~/.ssh/authorized_keys`.  Let's see if it worked.  We enter `ssh shell2017.picoctf.com ` and receive the flag.

#### Flag
`who_needs_pwords_anyways`
