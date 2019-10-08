Git Tutorial
============
A dummy repository to let other learn how to behave with git. It's just a short-form record. :)

### Tutorial
1. [গিট ব্যবহারের একেবারে প্রাথমিক জ্ঞান পর্ব ১ - tuts nano](http://tuts.nanodesignsbd.com/basics-of-git-1/) (Bengali : `bn_BD`)
2. [গিট ব্যবহারের একেবারে প্রাথমিক জ্ঞান পর্ব ২ - tuts nano](http://tuts.nanodesignsbd.com/basics-of-git-2/) (Bengali : `bn_BD`)
3. [গিট দিয়ে ভার্ষন নিয়ন্ত্রণ - git branch- tuts nano](http://tuts.nanodesignsbd.com/git-branching/) (Bengali : `bn_BD`)

### Install git
> http://git-scm.com/downloads

Download and Install.

### Reading List
* [**A successful Git branching model**](http://nvie.com/posts/a-successful-git-branching-model/) by *Vincent Driessen* (January 05, 2010)

### Tips & Tricks
* [**Today I Learned - Git**](https://github.com/jbranchaud/til#git)
* [**Git Tips**](https://github.com/git-tips/tips)
* [**How to find stuff in Git**](https://www.tygertec.com/find-stuff-git/)

### Cheatsheet
[**PDF:** Cheatsheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf) - training.github.com

---

### Configure git

```bash
git config --global user.name "Someone"
git config --global user.email "someone@example.com"
```

---
### Start git

```bash
mkdir GitTest
cd GitTest                              # enter the project directory
git init                                # initiate git
touch README (mate README?)
git add README                          # stage the file and its changes
git commit -m "first commit message"    # commit with a message
git remote add origin https://github.com/try-git/try_git.git    # HTTP origin
git remote add origin git@github.com:the_user/g.git             # SSH origin

```

---
### Clone repo

```bash
git clone http://path/to/repo.git               # clone a remote repo
git clone http://path/to/repo.git my-repo       # clone a remote repo to a specific directory
git clone <remote_repo_path> <directory_name>   # syntax
```

---
### Collaborate with git

```bash
cd existingrepository
git remote add origin git@github.com:the_user/g.git
git push -u origin master               # push local commits to the cloud
git remote -v                           # a list of a Git project's remotes

git fetch                               # fetch server changes to local repo *(but do nothing)*
git merge origin/master                 # merge the fetched changes to the master
git fetch && git log ..origin/master    # fetch server changes, and show the commit message
git log -p HEAD..FETCH_HEAD             # fetch server changes, show differences local-vs-remote
git pull                                # get and merge all the server changes

git show HEAD                           # see the HEAD commit
git checkout HEAD <file>                # restore the file to the last commit
git reset HEAD <file>                   # unstage that file from the staging area
git reset 5d69206                       # rewind to the specified SHA commit *(first 7 chars. of the 40 char SHA code)*
```

---
#### Undo the last commit

```bash
git commit -m "Something terribly misguided"
git reset --soft HEAD~                  # back to the stage as it were before committing
git add
git commit

```

---
#### Git tags

```bash
git tag -a v1.2 9fceb02                 # mark with tag to a specific commit
git tag                                 # show the list of tags
git push origin --tags                  # push all the tags to remote server
git tag -d v1.2                         # delete the tag specified, locally
git push origin :v1.2                   # delete the tag on remote server by sending empty tag
```

---
#### Git stash

```bash
git stash                               # store changes in a dummy local storage
git stash save "Stash Message"          # store changes with a message to remember
git stash list                          # check the stashed dummy commits
git stash show -p stash@{1}             # show the second stash item
git stash pop                           # apply the stashed data
git stash clear                         # clear all the stashed dummy commits
```

---
#### Git branching, diff and merging

```bash
git branch                              # Check the branches

git branch <branch_name>                # Make a new branch
git checkout <branch_name>              # Get to the new branch
git checkout master                     # Get back to the master branch
git checkout -b <branch_name>           # Shorthand: Create new branch and move onto it

git push origin <branch_name>           # push your branch up, to the remote, origin

git merge <branch_name>                 # Being in `master` merging new branch to `master`

## Rename git branch
git branch -m <oldname> <newname>

## Delete git branch
git branch -d <branch_name>             # Delete local branch
git push origin :<remote_branch_name>   # Delete a remote branch

## Show differences between two file over two branches
git diff <branch1>:<file_name.ext> <branch2>:<file_name.ext>
git difftool <branch1>:<file_name.ext> <branch2>:<file_name.ext>  # If Git DiffTool is configured

## Merge a specific file or bunch of files from another branch
git checkout <branch1>                  # First, get to the secondary branch
git checkout <branch2> <path_to_file>/<file_name.ext>
git commit -m "Merged a file from Primary branch"

## Showing which files have changed between two branches
git diff --name-status <parent>                       # Being in a feature branch, display file changes with master
git diff --name-status <firstbranch>..<secondbranch>  # Being in any branch, check differences between two branches

## Showing what exactly changed in a file between two branches
git diff <master> <childbranch> -- <path/to/file.ext> # Show changes made in childbranch in comparison to master branch

## Push git branch to all Remotes
git remote | xargs -L1 -I R git push R <branch>       # push to all remotes
```

---
### Git Local Sharing and Local Server setup

```bash
git --bare init                                           # instead of init it will create a base, not a repo
git remote add origin file:////pc65/test-directory        # local access to the folder required
```
---
### Git Patch
A file containing changes that can be shipped elsewhere to be merged
```bash
git checkout -b feature/feature-name                    # create a new branch for a feature
# do your changes in a branch
git format-patch master --stdout > my-changes.patch     # create a patch from this branch in contrast to 'master' branch, with the name 'my-changes.patch'
git apply --stat my-changes.patch                       # take a look what changes are in this patch
git apply --check my-changes.patch                      # check, before applying whether it could be merged easily or there is any conflict
```

#### Variations
```bash
# git format-patch -<n> <SHA1>
git format-patch -1 <sha>                               # create a patch only containing the diffs of a specific commit
git format-patch -1 <sha> path/to/file.js               # create a patch only containing the diffs of a specific file from a commit
```

#### Apply the Patch
```bash
git am < my-changes.patch                               # apply the patch
git am --signoff < my-changes.patch                     # apply the patch with signed off by the user
# or, simply apply
git apply my-changes.patch                              # apply the patch, if no conflict
```
#### If conflicted
```bash
git apply --reject --whitespace=fix my-changes.patch    # this will apply changes where there is no conflicts. There will be some .rej files where it fails to resolve conflicts
# resolve the conflicts manually where failed, comparing with the .rej files
git am --resolved                                       # if any resolve in underway, do it when you resolved the issues
```

---
### Git Backup

```bash
git bundle create my-project.bundle --all                # bundle all the branches into a single file as a backup
create my-project.bundle -b master                       # bundle only the master branch into a single file for backup

git init
git pull my-project.bundle master                        # extract bundle file to complete repository
```

---
### Git Alias
Find out the ~/.gitconfig file in your user's local directory and set the alias

```bash
[alias]
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --branches
```
---
<sup>Mayeenul Islam - <time class="updated" datetime="2019-07-24T11:00:00+06:00">201907241100</time></sup>
