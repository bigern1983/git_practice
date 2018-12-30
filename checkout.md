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

### New branches
Git checkout works hand in hand with git branch. The branch command can be used to create new branches, when starting a new feature you need to create a new branch off of master using `git branch <new branch>`. Once created you can check it out `git checkout <new branch>`. Alternatively `git checkout -b <new branch>` will create and checkout your new branch. 

```
#create and checkout a new branch
git checkout -b <branch>
```
The above command will create a new branch based off the current HEAD commit. 
```
git checkout -b <new branch> <existing branch>
```
This will create a new branch based off <existing branch> rather than HEAD. 

Switching branches is easy 
```
git checkout branch
``` 
switches to HEAD to the tip of branch.

### Detached Head State
HEAD is gits way of refering to the current snapshot. Internally the checkout command simply updates the HEAD to point to either the specified branch or commit. When it points to a branch git is happy, but when you checkout a specific commit it switches to a detached head state. 

This means that everything you are doing is detached from the rest of the project. If you develop in a detached head state there would be no branch allowing you to get back to it. When you checkout another branch there would be no way to reference the feature you have just developed. 

Never develop in a detached head state, do it in a new branch. 

However its fine to be in a detached head state simply to have a look at your old code. 

```bash
$ git log --oneline
4248463 (HEAD -> master, origin/master) more notes on branching checkout and merging
df3ec2d changed syntax highlighting to bash
8c83b17 finished branches notes
47e1224 deleted README.txt
75e6688 Merge branch 'dev'
9d6cf10 added README
c66f7a8 added checkout notes
fa10bd1 updated notes
4016232 added branching and undoing notes
69c275b testing
16058f0 commit

blahblahblah-4IL8K0L MINGW64 ~/git_practice (master)
$ git checkout 69c275b
Note: checking out '69c275b'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 69c275b testing

blahblahblah-4IL8K0L MINGW64 ~/git_practice ((69c275b...))
$ git status
HEAD detached at 69c275b
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        branches.md.saved.bak

nothing added to commit but untracked files present (use "git add" to track)

blahblahblah-4IL8K0L MINGW64 ~/git_practice ((69c275b...))
$ git checkout master
Previous HEAD position was 69c275b testing
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

blahblahblah-4IL8K0L MINGW64 ~/git_practice (master)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        branches.md.saved.bak

nothing added to commit but untracked files present (use "git add" to track)

blahblahblah-4IL8K0L MINGW64 ~/git_practice (master)
```

Checking out an old commit will put you in a detached head state, from here you can start a new branch or checkout another branch to get out of the detached head state. 

