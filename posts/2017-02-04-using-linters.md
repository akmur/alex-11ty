---
layout: single.njk
title: Using Linters
author: akmur
type: post
date: 2017-02-04T12:30:36+00:00
excerpt: |
  What is a linter?

  According to google, the definition of "lint" is "short, fine fibres which separate from the surface of cloth or yarn during processing."

  However for us programmers a linter is a software that checks your code for errors, bad practices and issues and gives you a warning when you make a mistake. A linter can be configurable according to rules that you decide.
url: /posts/1051/using-linters/
featured_image: https://vccw.test/wp-content/uploads/2017/02/wft93lgawwe-nick-casale.jpg
geo_latitude:
  - 45.518422
timeline_notification:
  - 1549152157
publicize_twitter_user:
  - akmur
publicize_linkedin_url:
  - "https://www.linkedin.com/updates?discuss=&scope=5122212&stype=M&topic=6233623980012511232&type=U&a=ydeS"
publicize_google_plus_url:
  - https://plus.google.com/+AlessandroMuraroIT/posts/R6AJG2vsbca
geo_longitude:
  - 9.174891
categories:
  - Articles
---

### What is a linter?

According to google, the definition of &#8220;lint&#8221; is *&#8220;short, fine fibres which separate from the surface of cloth or yarn during processing.&#8221;*

However for us programmers a **linter** is a software that checks your code for errors, bad practices, bad formatting and logical issues, and gives you a warning when you make a mistake. A linter can be configurable according to rules that you decide.

### **Why use a linter?**

Well, there are quite a few reasons:

- to write better code
- to write good code more easily
- to learn a programming language
- to write code aesthetically consistent
- to follow conventions
- to share code within a team without losing your mind

Let me double stress the fact that linters are especially important if you work in a team (meaning not alone), because by following some rules you can make sure that your code looks the same regardless of who's writing the code.

And finally, let me triple stress that linters are super good to learn how to code as they point out issues while you type (I especially find JavaScript linters useful for this reason).

### How does a linter look like?

A (JavaScript) linter looks like this (screenshot courtesy of <a href="https://code.visualstudio.com/Docs/languages/javascript" target="_blank" rel="noopener noreferrer">Visual Studio Code by Microsoft</a>). Please notice the warning in the lower part of the screen. By clicking on the error there, you can get to the line containing the issue.
The error position is also specified within parenthesis, in this case it is 7,12 (line 7, char 12).

<img class="aligncenter wp-image-1081 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2017/02/javascript_eslint_warning-1024x523.png" alt="javascript_eslint_warning" width="640" height="327" srcset="https://vccw.test/wp-content/uploads/2017/02/javascript_eslint_warning-1024x523.png 1024w, https://vccw.test/wp-content/uploads/2017/02/javascript_eslint_warning-300x153.png 300w, https://vccw.test/wp-content/uploads/2017/02/javascript_eslint_warning-768x392.png 768w, https://vccw.test/wp-content/uploads/2017/02/javascript_eslint_warning.png 1194w" sizes="(max-width: 640px) 100vw, 640px" />

While a sass linter looks like this (screenshot courtesy of <a href="http://stackoverflow.com/questions/41420931/sass-lint-yml-disabled-rules-are-showing-as-infos-rather-than-absent" target="_blank" rel="noopener noreferrer">Stack Overflow</a>)

<img class="wp-image-1085 size-large aligncenter" src="https://muraro.xyz/wp/wp-content/uploads/2017/02/hd1qq-1024x990.jpg" alt="hd1qq" width="640" height="619" srcset="https://vccw.test/wp-content/uploads/2017/02/hd1qq-1024x990.jpg 1024w, https://vccw.test/wp-content/uploads/2017/02/hd1qq-300x290.jpg 300w, https://vccw.test/wp-content/uploads/2017/02/hd1qq-768x743.jpg 768w, https://vccw.test/wp-content/uploads/2017/02/hd1qq.jpg 1492w" sizes="(max-width: 640px) 100vw, 640px" />

### How to use a linter?

Depending on your tool of choice, there are different ways to install and use a linter. To have a working linter for JavaScript and Sass, you need to:

- Install <a href="https://nodejs.org/en/" target="_blank" rel="noopener noreferrer">Node</a> on your machine if you haven't already.
- Install the linters globally using the node package manager (aka NPM)
  - to install ESlint (the JavaScript linter): `npm install -g eslint`
  - to install Sass lint: `npm install -g sass-lint`
- Install the linter plugin in your editing software
  - In <a href="https://code.visualstudio.com" target="_blank" rel="noopener noreferrer">Visual Studio Code</a>, here is the <a href="https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint" target="_blank" rel="noopener noreferrer">ESlint</a> package, and here is <a href="https://marketplace.visualstudio.com/items?itemName=glen-84.sass-lint" target="_blank" rel="noopener noreferrer">Sass Lint</a> Package
  - In Atom, here is the <a href="https://atom.io/packages/linter-eslint" target="_blank" rel="noopener noreferrer">ESlint</a> package, and here the <a href="https://atom.io/packages/linter-sass-lint" target="_blank" rel="noopener noreferrer">Sass Lint</a> Package
  - In Sublime Text, here is <a href="https://github.com/polygonplanet/sublime-text-eslint" target="_blank" rel="noopener noreferrer">ESlint</a> and here is <a href="https://github.com/skovhus/SublimeLinter-contrib-sass-lint" target="_blank" rel="noopener noreferrer">Sass lint</a>.
- Create a linting configuration file for each language you need to lint
- Restart your code editor just to be safe.

### Wait, what are these linting configuration files?

Linters need configuration files in order to give instructions to our linters about how we want the linter to behave. To get started, you can use some default linter configurations, and when you grow more accustomed to their usage you can change these defaults. You have to place these config files in the **root of your project** for it to be recognised by the code editor.

### How to create a linter configuration file?

#### ESlint

Go to your project folder using your Terminal, and type:

<pre class=" language-bash"><code>eslint &lt;span class="token operator"&gt;--&lt;/span&gt;init </code></pre>

This will start a little program that will ask you a few questions. The first question you get is the following, just press enter to proceed.<figure id="attachment_1133" aria-describedby="caption-attachment-1133" style="width: 640px" class="wp-caption aligncenter">

<img class="wp-image-1133 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-15-59-1024x154.png" alt="screen-shot-2017-02-04-at-13-15-59" width="640" height="96" srcset="https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-15-59-1024x154.png 1024w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-15-59-300x45.png 300w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-15-59-768x116.png 768w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-15-59.png 1498w" sizes="(max-width: 640px) 100vw, 640px" /> <figcaption id="caption-attachment-1133" class="wp-caption-text">Eslint wants answers</figcaption></figure>

Then you'll be asked a bunch of additional question, choose whatever you want:<figure id="attachment_1137" aria-describedby="caption-attachment-1137" style="width: 640px" class="wp-caption aligncenter">

<img class="wp-image-1137 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-17-29-1024x350.png" alt="screen-shot-2017-02-04-at-13-17-29" width="640" height="219" srcset="https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-17-29-1024x350.png 1024w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-17-29-300x103.png 300w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-17-29-768x263.png 768w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-17-29.png 1544w" sizes="(max-width: 640px) 100vw, 640px" /> <figcaption id="caption-attachment-1137" class="wp-caption-text">More eslint questions</figcaption></figure>

This will create a _.eslintrc.json_ file which will look like this:<figure id="attachment_1146" aria-describedby="caption-attachment-1146" style="width: 356px" class="wp-caption aligncenter">

<img class="alignnone wp-image-1146" src="https://muraro.xyz/wp/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-21-14.png" alt="screen-shot-2017-02-04-at-13-21-14" width="356" height="475" srcset="https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-21-14.png 510w, https://vccw.test/wp-content/uploads/2017/02/screen-shot-2017-02-04-at-13-21-14-225x300.png 225w" sizes="(max-width: 356px) 100vw, 356px" /> <figcaption id="caption-attachment-1146" class="wp-caption-text">.eslintrc.json</figcaption></figure>

That's it, you got a working ESlint configuration.

### Sass lint

You can find a sample configuration file here [on the official repository][1]. Download the file and add it to your root.

### More linters

Linters are available for any coding language, and the installation steps are similar to these ones, although almost certainly slightly different.

**Good luck!**

[1]: https://github.com/sasstools/sass-lint/blob/master/docs/sass-lint.yml
