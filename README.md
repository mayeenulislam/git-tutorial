Git Tutorial
============
A dummy repository to let other learn how to behave with git :)

###Install git###
> http://git-scm.com/downloads

Download and Install.

---

###Configure git###
<pre>
git config --global user.name "Name"
git config --global user.email "s.s@s.com"
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
git remote and origin git@github.com:the_user/g.git
git push -u origin/master
git push origin master
</pre>
---
###Collaborate with git###
<pre>
cd existingrepository
git remote add origing git@github.com:the_user/g.git
git push -u origin master
</pre>
---
