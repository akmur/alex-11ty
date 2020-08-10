---
layout: single.njk
title: A collection of useful git commands
author: akmur
type: post
date: 2012-10-18T23:38:32+00:00
tags:
  - Article
  - Tutorial
  - Git
---

In my previous article I have introduced the basic concepts around the awesome Git. [Check it out][1] if you are not sure what we are talking about.

If you do, but you are not a Git ninja (yet), you might find the following commands useful in your everyday work. They are not super advanced but they might be useful.

**git status**
Useful to assess the current status of your branch. Where am I? What am I doing? Stuff like that.

**git pull**
to get latest code from repo

**git pull origin branchname**
to get latest code for a single branch which resides on the "origin" tree

**git fetch**
imagine a friend of yours branched off to a new branch, called "myawesomebranch". How do you retrieve his code? Simply enough, run git fecth to retrieve a list of all remote branches. Then with the next command, you'll be able to "download" that branch to your computer.

**git fetch origin branchname:branchname**
to fetch a new branch (for example, git fetch origin myawsomebranch:myawesomebranch)

**git checkout -b myfeature master**
If you want to start working in a brand new branch, this is the command for you. In this case you are creating a branch called "myfeature", and you're branching off the "master" branch.

**git checkout development**
To switch between branches, this is the command to run. In this case you would switch to the branch "development"

**git merge &#8211;no-ff myfeature**
If you want to merge the work you've done in your own branch with an existing branch, this is the command for the job (just be careful of possible conflicts). In this case you would merge the branch "myfeature" with the branch you're currently in.

**git branch -d myfeature**
Delete a branch with this command

**git push origin :new_feature_name**
delete a branch on origin (on the "server")

**git checkout 56e05fced214c44a37759efa2dfc25a65d8ae98d**
to revert to an earlier specified commit, use the above (each commit has a code like the one above which i made up). You can see such codes by looking at the repository online or by using a visual tool like gitk (on ubuntu/Linux)

**git reset 56e05fcede05fcede05fced**
reset your work to the desired commit

**git revert HEAD**
revert to the last commit

**git revert HEAD^**
revert to the next-to-last commit

**git reset**
to reset in case you wrongly added files to commit, example: git reset db/schema.rb would remove this file from the files to be committed

**git rm \$(git ls-files &#8211;deleted)**
When you delete files, they stay in your GIT history unless you remove them from there too. This is the right command.

And i think this is a pretty good list of git commands, don't you think?
Happy gitting!

[1]: http://localhost/alex/posts/an-introduction-to-git/ "An introduction to GIT"
