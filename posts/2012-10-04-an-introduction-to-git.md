---
layout: single.njk
title: An introduction to GIT
date: 2012-10-04T21:18:32+00:00
url: https://alexmuraro.me/posts/2012-10-04-an-introduction-to-git/
excerpt: "I've recently been explaining the basics of git to a new colleague of mine, and while it is quite easy to use, I understand that at first it's not very intuitive, so I got the idea for this short tutorial on its usage, trying to stay quick and to the point, as usual."
tags:
  - Articles
  - Tutorial
  - Git
---

I've recently been explaining the basics of git to a new colleague of mine, and while it is quite easy to use, I understand that at first it's not very intuitive, so I got the idea for this short tutorial on its usage, trying to stay quick and to the point, as usual.

**What is GIT?**
From [Git's homepage][1]: "Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency."
In other words, it's a little software capable of keeping track of changes to our files, making it possible to revert to older versions. Also, another basic cool feature is that it allows you to "branch" off a main tree and develop you own feature, without getting in the way of other developers, and then gives you ways to reintegrate your changes into the main tree.

The good thing is that it **doesn't need the internet** to work, as you can set up a local repository on your machine and take advantage of Git's great features for versioning. of course to collaborate in a team, you do need the internet.

**How do I install Git?**
I think a good page about installing and setting up Git, can be found on [github's "set up git" page][2]. Follow it, then come back.

**Getting started**
If you've followed the Github's tutorial, you'll be ready to get your work started.
Imagine you have a rails project, or a php project, or whatever you have. Open you Terminal and browse to your folder. (Need help with the terminal? maybe this video can help)

so in my case i would type in terminal

```
cd Projects/myapp
```

Now I am in my project folder. I have to initialize my project with git, and to do this i type:
`git init`

A good idea to get started is to do what is called a "commit" of our whole project. Here are the two commands to type:

```
git add .
git commit -m "my first commit, hooray"
```

With these two commands we have added all of the content of our folder (first line) and then we have committed our changes by adding a little explanation (second line).

Now we've started our repository, and added our files. Basically we should repeat the commands above each time we make a (major) modification to our code, think of it as a milestone. We can make as many commits as we want of course, and also keep in mind that finer control is available throughmore specific commands,
For example, we may want to only commit a single file, in which case we would do something like:

```
git add foldername/foldername/myfile.htm
```

**Sharing with collaborators**
Now you might want to have your stuff saved online, maybe to collaborate with your friends. To do this, you first have to create your own repository on a website like [Github][3] or [Bitbucket][4]. I know Github is hip and social, but I dig Bitbucket. Either way, it's cool. The main difference being that Github's free account are public and its attitude is toward social sharing, while Bitbucket gives you free private account and it's attitude is toward personal and private projects.

So, go to one of those website, (for example Bitbucket), create an account, then click on "Create a repo", and finally, copy that little url after "git clone" (it would look like https://yourname@bitbucket.org/yourname/yourrepo). That is the address to your repository.

Now, back to the terminal, type the following (but replace the URL with your own):

```
git remote add origin https://you@bitbucket.org/..etc
```

and then

```
git push origin master
```

to push your code online. Hooray, it's now online. If you add people to your Bitbucket account, they will be able to copy your code to your hard drive by typing in terminal:

```
git clone https://your-repo-url
```
