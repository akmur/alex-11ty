---
layout: single.njk
title: Switching from WordPress to Eleventy
author: akmur
type: post
date: 2020-08-10T15:47:16+00:00
featured_image: /assets/images/11ty.jpg
url: https://alexmuraro.me/posts/2020-08-11-switching-from-wordpress-to-eleventy/
excerpt: Here I talk about my (fast) journey switching from WordPress to Eleventy, a barebones but feature-rich JavaScript static site generator. In this article there is no code because I think whatever you need can be seen in the repository for this site.
tags:
  - Tutorial
  - JavaScript
  - WordPress
  - Articles
---

### What is this article about?

Here I talk about my (fast) journey switching from WordPress to [Eleventy](https://www.11ty.dev/), a barebones but feature-rich JavaScript static site generator. In this article there is no code, because I think whatever you need can be seen in the [repository](https://github.com/akmur/alex-11ty) for this site, and anyway there are tutorials out there already, like [this one](https://giustino.blog/how-to-build-a-website-with-eleventy-and-deploy-it-on-netlify/).

### The Situation

I've always liked moving between platforms for this blog, and I've tried a few along the years: a self hosted WordPress installation, a ready made wordpress.com solution, a custom solution made with React and Contentful, and last year I settled for a static site generated starting from a local WordPress installation.

This worked fine, and I didn't have many complaints about it, except for one thing. There was a barrier about thinking about some content to add, or modifications to make to the theme, and going online. That barrier was the fact that I had to:

- connect my external SSD where I keep Virtual Machines.
- fire up the Vagrant installation containing my Wordress site.
- make my changes or write a post.
- fight with the WordPress editor which doesn't like code snippets.
- push a button and generate a static version of the WordPress site.
- drag and drop the generated static files to Netlify (because I didn't want to pay for the pro version of static generator).

As you can see, not difficult, but convoluted.
If I felt like changing some CSS... I just wouldn't do it. If I wanted to write a blog post, I would probably not do it as well.

### The Idea

My colleague and friend [https://giustino.blog](Giustino), whose technical tutorial I linked above, gave me the inspiration I needed to switch from my WordPress setup to [Eleventy](https://www.11ty.dev/). I read on Twitter he was about to write a book about Eleventy and since I already started playing around with Eleventy last year and got good vibes, but never did anything with it, I decided to actually do it and migrate to it.

### Why Eleventy

There are a few compelling reasons for Eleventy.

- I can write in Markdown.
- The setup is simple.
- The integration with Netlify or Github pages is very simple.
- The layout system is also very simple.
- For my use case, barrier from thought to post is lower than with WordPress.
- While I write or edit content, Eleventy will watch for changes and save everything to the `_site` folder. If you then push to Github, and you have linked Github with Netlify, the content of the `_site` folder will be automatically served.

### The Process

So, once I had this idea, I proceeded as follows:

- I installed [Eleventy](https://www.11ty.dev/) globally and made sure it was working.
- Using the [WordPress to Hugo Exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter) I exported all my posts to Markdown files. Probably there are other plugins that do the same job, but I just used this one. Then, the most painful part, has been to go and edit the meta information of each post in case it was wrong or outdated.
- I started creating all the layout parts that would make my site, by copying chunks of php files from WordPress to Eleventy. Eleventy uses [nunjucks](https://mozilla.github.io/nunjucks/) files by default but you can use something else if you want. Me, I couldn't be bothered so I went with `nunjucks`. In any case, you will need to adjust your `php` templates to whatever template engine you decide to use.
- I copy-pasted my css file to my new website.
- Very important: you will need to edit the `.eleventy.js` file to allow for css to be copied to the `_site` folder.
- In the process, I removed a ton of unused images. Right now only a handful of posts have images, and I like it like that. I can always start adding exactly what I need at any point in the future.
- I deployed to Netlify.

### How long did it take

It took me about 6 hours all considered. 2 hours to actually setup Eleventy and port my theme from WordPress, and 3/4 hours to adapt my markdown files and review them.

The result is the site you are reading. So exactly the same as before, but faster, easier to edit, more fun to modify.

### The Github repository

Here is the [Github repository](https://github.com/akmur/alex-11ty) for this website. Feel free to have a look. Hopefully the setup is self explainatory. There are more things one can do with Eleventy, but for my use case I didn't need to dig too deep.

---

<span>Photo by <a href="https://unsplash.com/@davidmonje?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">David Monje</a> on <a href="https://unsplash.com/s/photos/eleven?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>
