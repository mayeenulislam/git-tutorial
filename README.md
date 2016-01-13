Git Tutorial
============
A dummy repository to let other learn how to behave with git. It's just a short-form record. :)

### Tutorial
1. [গিট ব্যবহারের একেবারে প্রাথমিক জ্ঞান পর্ব ১ - tuts nano](http://tuts.nanodesignsbd.com/basics-of-git-1/) (Bengali : `bn_BD`)
2. [গিট ব্যবহারের একেবারে প্রাথমিক জ্ঞান পর্ব ২ - tuts nano](http://tuts.nanodesignsbd.com/basics-of-git-2/) (Bengali : `bn_BD`)

### Install git
> http://git-scm.com/downloads

Download and Install.

---

### Configure git

```
git config --global user.name "Someone"
git config --global user.email "someone@example.com"
```
---
### Start git

```
mkdir GitTest
cd GitTest
git init
touch README (mate README?)
git add README
git commit -m "first commit message"
git remote add origin https://github.com/try-git/try_git.git
git remote add origin git@github.com:the_user/g.git
git push -u origin/master
git push origin master
```
---
### Collaborate with git

```
cd existingrepository
git remote add origin git@github.com:the_user/g.git
git push -u origin master

git fetch && git log ..origin/master    # fetch server changes, and show the commit message
git log -p HEAD..FETCH_HEAD             # fetch server changes, show differences local-vs-remote
git pull                                # get and merge all the server changes
```

#### Git stash
```
git stash								# store changes in a dummy local storage
git stash list							# check the stashed dummy commits
git stash clear							# clear all the stashed dummy commits
```
#### Git branching

```
git branch 								# Check the branches

git branch branch_name					# Make a new branch
git checkout branch_name				# Get to the new branch
git checkout master						# Get back to the master branch
git checkout -b branch_name				# Shorthand: Create new branch and move onto it

git merge branch_name 					# Being in `master` merging new branch to `master`

git branch -d branch_name				# Delete local branch
git push origin :remote_branch_name		# Delete a remote branch
```
---
### Git Local Sharing and Local Server setup

```
git --bare init                                           # instead of init it will create a base, not a repo
git remote add origin file:////pc65/test-directory        # local access to the folder required
```

---
