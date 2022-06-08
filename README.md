# gitful-things
some needful things for git


## stop tracking a file
Files present in the repository will be tracked even though they are added to a gitignore (post-commited). Stop tracking a <file> (which will not be staged for any future commit) using:

`git update-index --assume-unchanged <file>`

Invoking the above statement on a file results in the said file not being queued into any push (upstream), i.e., it will not be added and pushed into any further commit. This may be useful when adding a "blank config" file to a repository for demonstration purposes but for (local) testings login credentials may be required which obviously should not be exposed to the broad internet-light.

Please note that the file must be in the repository (git add, git push), else the error `fatal: Unable to mark file <file>` is returned.
