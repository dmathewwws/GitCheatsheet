#GIT

  ##Going beyond push, pull and commit, tools for avoiding file and storyboard conflicts when working with iOS/XCode
    ###>> git stash
      To change branches without having to make a commit
      ####>> git stash list
      ####>> git stash apply
        goes back to stash, watch for conflicts if you continue to work on the branch without applying the stash back on and          then try to apply stash
        #####>> git stash apply stash@{2}
        will go back to stash index 2
        #####Can reapply to another branch, read up for rules and conflicts
        http://git-scm.com/book/en/v1/Git-Tools-Stashing
      ####>> git stash save "your message here"
      ####>> git stash drop stashid
        delete the stash (before or after applying)
    ###>> .gitignore
      http://github.com/github/gitignore/blob/master/Objective-C.gitignore
      ####may want to add dstore to your gitignore file
        http://gist.github.com/octocat/9257657
      ####>> git rm --cached filename
        this removes a file from git tracking, now you can put it in the .gitignore file
      ####>> touch .gitignore
        do this inside directories you want to be tracked but are not currently being tracked because they are empty (empty           folders are not tracked by default)
    ###Local and Remote Branches
      ####>> git branch -a
        lists all local and remote branches
      #####>> git branch -r
        lists only remote branches
      ####>> git push origin origin:ref/heads/branchname
        this creates a new remote branch
      ####>> git push origin :branchname
        this deletes the branch from the origin remote
        #####>> git checkout --track -b branchname origin/branchname
          start tracking new branch so that you get the latest updates on pulls
      ####>> git branch -d branchname
        this deletes the branch locally
    ###>> git reset --hard 
      go back to a previous commit, deletes your current state, also achieved with >> git checkout -f
      ####>> git reset --hard 2393982
        this will reset to the commit id starting with these numbers. You do not need the whole commit id, only the first few characters as they are unique.
####>> git reset --soft
as above but not a permanent move, will not delete the current state, return using the commit
###>> git log
shows the log of commits
####>> git log --pretty=oneline --graph --all
shows all commits and merges, good way to find unmerged commits or visualize your branch history
####>> git cherry
tells us which commits are not in the current branch
###Dealing With Potential Conflicts
####>> git checkout filename
this allows you to commit without including the file, the changes in the file are reset, if you have a filename the same as a branch name use >> git checkout -- filename instead
####>> git update-index --assume-unchanged filename
temporarily ignore a file, it will remain ignored until you add it back to the index, this means it will not be merged.
#####>> git update-index --no-assume-unchanged filename
this adds the file back to the index, must do this is you want to merge your file
####>> git checkout --ours filename
this will tell git to keep our file if there is a conflict with a branch we are merging into
####>> git checkout --theirs filename
this will keep their file instead of ours
###>> git fsck --lost-found
if you reset --hard and realize that you actually needed the changes, the commit is not deleted immediately, it is "dangling". Use this to get the commit id and then >>git merge 2930923 will forward you back to the commit
