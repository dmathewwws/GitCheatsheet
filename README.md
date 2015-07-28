#GIT

###Dealing With Potential Conflicts#
####>> git diff filename
this will show the changes to your file in Terminal
####>> git checkout filename
this allows you to commit without including the file, the changes in the file are reset, if you have a filename the same as a branch name use >> git checkout -- filename instead
####>> git checkout --ours filename
this will tell git to keep our file if there is a conflict with a branch we are merging into
####>> git checkout --theirs filename
this will keep their file instead of ours
