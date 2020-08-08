---
layout: layout.njk
title: An introduction to GIT
---

I&#8217;ve recently been explaining the basics of git to a new colleague of mine, and while it is quite easy to use, I understand that at first it&#8217;s not very intuitive, so I got the idea for this short tutorial on its usage, trying to stay quick and to the point, as usual.

**What is GIT?**
From [Git&#8217;s homepage][1]: &#8220;Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.&#8221;
In other words, it&#8217;s a little software capable of keeping track of changes to our files, making it possible to revert to older versions. Also, another basic cool feature is that it allows you to &#8220;branch&#8221; off a main tree and develop you own feature, without getting in the way of other developers, and then gives you ways to reintegrate your changes into the main tree.

The good thing is that it **doesn&#8217;t need the internet** to work, as you can set up a local repository on your machine and take advantage of Git&#8217;s great features for versioning. of course to collaborate in a team, you do need the internet.

**How do I install Git?**
I think a good page about installing and setting up Git, can be found on [github&#8217;s &#8220;set up git&#8221; page][2]. Follow it, then come back.

**Getting started**
If you&#8217;ve followed the Github&#8217;s tutorial, you&#8217;ll be ready to get your work started.
Imagine you have a rails project, or a php project, or whatever you have. Open you Terminal and browse to your folder. (Need help with the terminal? maybe this video can help)

so in my case i would type in terminal

```js
cd Projects/myapp
```

Now I am in my project folder. I have to initialize my project with git, and to do this i type:
`git init`

A good idea to get started is to do what is called a &#8220;commit&#8221; of our whole project. Here are the two commands to type:

```js
git add .
git commit -m "my first commit, hooray"
```

With these two commands we have added all of the content of our folder (first line) and then we have committed our changes by adding a little explanation (second line).

Now we&#8217;ve started our repository, and added our files. Basically we should repeat the commands above each time we make a (major) modification to our code, think of it as a milestone. We can make as many commits as we want of course, and also keep in mind that finer control is available throughmore specific commands,
For example, we may want to only commit a single file, in which case we would do something like:

```js
git add foldername/foldername/myfile.htm
```

**Sharing with collaborators**
Now you might want to have your stuff saved online, maybe to collaborate with your friends. To do this, you first have to create your own repository on a website like [Github][3] or [Bitbucket][4]. I know Github is hip and social, but I dig Bitbucket. Either way, it&#8217;s cool. The main difference being that Github&#8217;s free account are public and its attitude is toward social sharing, while Bitbucket gives you free private account and it&#8217;s attitude is toward personal and private projects.

So, go to one of those website, (for example Bitbucket), create an account, then click on &#8220;Create a repo&#8221;, and finally, copy that little url after &#8220;git clone&#8221; (it would look like https://yourname@bitbucket.org/yourname/yourrepo). That is the address to your repository.

Now, back to the terminal, type the following (but replace the URL with your own):

```js
git remote add origin https://you@bitbucket.org/..etc
```

and then

```js
git push origin master
```

to push your code online. Hooray, it&#8217;s now online. If you add people to your Bitbucket account, they will be able to copy your code to your hard drive by typing in terminal:

```js
git clone https://your-repo-url
```
