## git reset

Good way to undo changes in private repo that haven't been shared. 

* **--soft**
  - The staged snapshot and working directory are not altered
* **--mixed**
  - staged snapshot is updated but the working directory is not changed (default)
* **--hard**
  - staged snapshot and the working directory are both updated to match the specified commit. 

Moves head to previous commit 


## git checkout

Move head and update working directory. 

If you checkout and then make commits you should create a new branch

Can be used with specific files as follows:-

```
#get old copy of file
git checkout HEAD~1 foo.py
#add it to staging area
git add foo.py
#commit changes 
git commit -m "undid some changes to foo.py"
```


## git revert

Revert undoes a commit by creating a new commit. 

This undoes changes by creating a new commit, preserves the history. 



  

  
  

