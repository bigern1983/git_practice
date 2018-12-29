## Git Merge

Git merge will combine multiple sequences of commits into one unified history. 

Usually git merge is used to combine two branches. 

Git merge takes 2 commit pointers and will find a common base commit between them. It will then create a new merge commit that combines the changes of each queued merge commit sequence. 

### Prepare to merge

Before merging there are a couple of steps to ensure the merge goes smoothly. 

* **Confirm the receiving branch**
  - Run git status to ensure that HEAD is pointing to the correct merge receiving branch. 
  - If needed execute git checkout receiving branch.

* **Fetch the latest remote commits** 
  - Make sure the receiving branch and merging branch are upto date with the remote repo. 
  - git fetch to pull the latest remote commits. 
  - git pull to ensure master branch is upto date. 

### Merging

* Once prepared to merge run git merge branch name where branch name is the name of the branch that will be merged into the current receiving branch. 

```
#start a new branch 
git checkout -b test_branch master
#add some files
git add <file>
git commit -m "new feature"
git add <file>
git commit -m "finished feature"
#prepare to merge
git checkout master
git pull origin master 
#merge
git merge test_branch
#delete test_branch
git branch -d test_branch

#if deleting branch on remote
git push --delete origin master
```

### Fast Forward Merge

If a linear path from the current branch to the top of the target branch exists git will execute a fast forward merge. It just moves the branch tip forwards up to the end end of the target branch. 

### 3 Way Merge

If there is no linear path, i.e. there are new features in both branches git has not choice but to perform a 3 way merge. 

### Conflicts

When the same parts of the same file are different in the branches git won't be able to figure out which version to keep. This is a conflict. 

When git finds a conflict it edits the required file to highlight the conflict. 

```
here is some content not affected by the conflict
<<<<<<< master
this is conflicted text from master
=======
this is conflicted text from feature branch
```


