# gitful-things
some needful things for git


## setting-up Git(hub)

### set username and email and tokens
git config --global user.email "claus@kovacs.cf"

git config --global user.name "Claus Kovacs"

git config --global github.token ghp_Token

Tokens may be generated at https://github.com/settings/tokens

### set ssh for Github (Ubuntu 22.04.1 LTS)
`cd ~/.ssh`

`ssh-keygen -o -t rsa -C "claus@kovacs.cf"`

Press <ENTER> for the next three prompts (which saves the generated key into *~/.ssh* and sets no (optional) passphrase). The shell log should look something like:

```
claus@raspPi1:~/.ssh$ ssh-keygen -o -t rsa -C "claus@kovacs.cf"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/claus/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/claus/.ssh/id_rsa
Your public key has been saved in /home/claus/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:n3lm97gIEOUWssbYK5pFgk0Vif2ZbokXhNqvaqE/onk claus@kovacs.cf
The key's randomart image is:
+---[RSA 3072]----+
|    .+o+. o      |
|   +. ++.= .     |
|  . oooo*oo      |
|    .o..=+       |
|      o+So       |
|    .+..*o o     |
|   .o. +  = + .  |
| .E o .    = o o |
|oo +oo      . o..|
+----[SHA256]-----+
```
Next, show the generated public key using `cat id_rsa.pub` and copy the whole output (starting from *ssh-rsa* to the end which contains the given email from the previous command).

Then log into Github, navigate Settings -> SSH and GPG keys, click on *New SSH key*, give it a recognizable name and paste the generated public key from the previous shell output.

Everything should work now, just keep in mind to clone any repository using the *SSH* option.

## stop tracking a file
Files present in the repository will be tracked even though they are added to a gitignore (post-commited). Stop tracking a <file> (which will not be staged for any future commit) using:

`git update-index --assume-unchanged <file>`

Invoking the above statement on a file results in the said file not being queued into any push (upstream), i.e., it will not be added and pushed into any further commit. This may be useful when adding a "blank config" file to a repository for demonstration purposes but for (local) testings login credentials may be required which obviously should not be exposed to the broad internet-light.

Please note that the file must be in the repository (git add, git push), else the error `fatal: Unable to mark file <file>` is returned.
