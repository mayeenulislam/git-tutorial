Git Tutorial
============
A dummy repository to let other learn how to behave with git. Will add inline details later, it's just a shorform record. :)

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
</pre>
---
