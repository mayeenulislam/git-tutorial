Git Tutorial
============
A dummy repository to let other learn how to behave with git. Will add inline details later, it's just a shorform record. :)

1. [গিট ব্যবহারের একেবারে প্রাথমিক জ্ঞান পর্ব ১ - tuts nano](http://tuts.nanodesignsbd.com/basics-of-git-1/)
2. [গিট ব্যবহারের একেবারে প্রাথমিক জ্ঞান পর্ব ২ - tuts nano](http://tuts.nanodesignsbd.com/basics-of-git-2/)

###Install git###
> http://git-scm.com/downloads

Download and Install.

---

###Configure git###
<pre>
git config --global user.name "Someone"
git config --global user.email "someone@example.com"
</pre>
---
###Start git###

<pre>
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
</pre>
---
###Collaborate with git###
<pre>
cd existingrepository
git remote add origin git@github.com:the_user/g.git
git push -u origin master

git fetch && git log ..origin/master    #fetch server changes, and show the commit message
git log -p HEAD..FETCH_HEAD             #fetch server changes, show differences local-vs-remote
git pull                                #get and merge all the server changes
</pre>
---
###Git Local Sharing and Local Server setup
```
git --bare init                                           # instead of init it will create a base, not a repo
git remote add origin file:////pc65/test-directory        # local access to the folder required
```
