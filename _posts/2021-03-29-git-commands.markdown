---
layout: post
title: 'Git Commands'
date: 2021-03-29 08:54:37 +0530
categories: DotNet, Github
---

**Git Rebase**

![](https://wac-cdn.atlassian.com/dam/jcr:e4a40899-636b-4988-9774-eaa8a440575b/02.svg?cdnVersion=1521)

Rebasing is changing the base of your branch from one commit to another making it appear as if you'd created your branch from a different commit.

https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase#:~:text=From%20a%20content%20perspective%2C%20rebasing,them%20to%20the%20specified%20base.

lenovo@Lenovo-PC MINGW64 /e/cosmos/Learning/Github/git-fast (master) </br>
$ git checkout -b feature-branch </br>
$ vim human.txt </br>
$ git commit -am "master: added team information - human.txt" </br>
$ git checkout -b top-feature

**top-feature** </br>
$ git checkout -b top-feature </br>
$ vim index.html </br>
$ git commit -am "top-feature : index.html"</br>
$ git commit -am "top-feature : index.html - browser upgrade recom"</br>

**master** </br>
$ git checkout master </br>
$ vim 404.html </br>
$ git commit -am "master: modifed tittle 404.html"</br>
$ vim 404.html </br>
$ git commit -am "master: modifed new tittle 404.html" </br>

lenovo@Lenovo-PC MINGW64 /e/cosmos/Learning/Github/git-fast (master)</br>
$ git log --oneline --decorate --graph --all </br>
* 9f6fa1d (HEAD -> master) master: modifed new tittle 404.html
* 566c9c9 master: modifed tittle 404.html
| * 40a671f (top-feature) top-feature : index.html - browser upgrade recom
| * 3c80809 top-feature : index.html
|/
* 69fe198 master: added team information - human.txt

$ git checkout top-feature </br>
$ git rebase master <br>
Successfully rebased and updated refs/heads/top-feature. </br>

```$ git checkout master </br>```

$ git merge top-feature </br>
Updating 9f6fa1d..0b1b00e
Fast-forward
index.html | 2 ++
1 file changed, 2 insertions(+)

$ git branch -d top-feature </br>
Deleted branch top-feature (was 0b1b00e).


**Git rebase with conflict** </br>
$ vim human.txt </br>
$ git commit -am "master: prior to rebase conflict" </br>
$ git checkout -b rebase-conflict </br>
$ vim index.html </br>
$ git commit -am "rebase-conflict : index.html" </br>
$ git checkout master </br>
$ vim index.html </br>
$ git commit -am "master : index.html" </br>
$ git log --oneline --decorate --graph --all </br>
* 7d163b7 (HEAD -> master) master : index.html
| * e185f9a (rebase-conflict) rebase-conflict : index.html
|/
* 6b616ca master: prior to rebase conflict </br>

$ git checkout rebase-conflict </br>
$ git rebase master </br>
$ git mergetool </br>
$ git rebase --continue </br>
$ git log --oneline --decorate --graph --all </br>

$ git checkout master </br>
$ git merge rebase-conflict </br>
$ git log --oneline --decorate --graph --all
* 905a294 (HEAD -> master, rebase-conflict) rebase-conflict : index.html
* 7d163b7 master : index.html

$ git branch -d rebase-conflict </br>
