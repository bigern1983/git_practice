## Git Checkout

Switch between different versions of an entity

Operates on 3 distinct entities:

* files
* commits
* branches

### Checking out branches

git checkout lets us navigate between branches created by git branch. Checking out a branch:

* updates all the files in the working directory to match the version stored in the branch
* tells git to record all new commits on the checked out branch

### Existing branches

See what branches exist and checkout one of them

```bash
#see what branches exist
>git branch
master
develop
>git checkout develop
```

