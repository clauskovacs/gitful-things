# gitful-things
some needful things for git


## stop tracking a file
Files present in the repository will be tracked even though they are added to a gitignore (post-commited). Stop tracking a <file> (which will not be staged for any future commit) using:

`git update-index --assume-unchanged <file>`
