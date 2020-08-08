---
layout: layout.njk
title: Switching this site to React + WordPress
author: akmur
type: post
date: 2019-02-05T09:39:13+00:00
url: /posts/1250/switching-this-site-to-react-wordpress/
featured_image: https://vccw.test/wp-content/uploads/2019/02/thierry-meier-219007-unsplash-e1549359137942.jpg
timeline_notification:
  - 1549359556
categories:
  - Articles
---

_UPDATE 15th of March 2019: The solution below works perfectl, except for the fact that social network sites won&#8217;t pick up the preview from your posts. For this reason i have opted to go back to a local WordPress installation, from which  a static version of the site is generated and deployed to Netlify. All this is done using [WP2Static][1] plugin._

Yesterday I have deployed a new version of my site. It looks exactly like before, but it has some important differences:

- I am using React + Reach Router instead of Vanilla JS and Navigo.js
- I ditched Contentful for <del datetime="2019-02-06T23:22:50+00:00">WordPress.com</del> a self hosted WordPress
- It is hosted on Netlify instead of Github Pages

### Why React + Reach?

When I started my personal site relaunch project, a couple of months ago, I tried out a number of solutions, including React, but in the end I decided to ditch everything and go the Vanilla route, as I felt React was overkill.
After having grown more accustomed with React though during the last month, I started feeling that the fun-factor would have increased by using React, so I did.
I then decided for [Reach Router][2] because it feels more friendly and less bloated than React Router.
So, in the end, I still think React is overkill, but the overall javaScript size is around 50Kb gzipped, which is acceptable I think.

### Ditching Contentful in favour of WordPress

When I started this new version of my blog, i went for [Contentful][3] at first. Partly because I wanted a very fast response, partly because I wanted to try out the new kid on the block.

However, after some playing around, I have resorted to using [WordPress][4], which provides APIs. The publishing experience is much more polished on WordPress, media management is way better, there is no usage-limit since it&#8217;s self hosted, and I own the data.
Granted, Contentful response feels maybe a bit faster, but that&#8217;s not a major concern.
I am using the cheapest managed hosting solution from NameCheap. not super fast perhaps, but for what I need, it&#8217;s fine.
Worth noting is the fact that you can also use APIs from their free wordpress.com service, but in that case the pages will not be crawlable by Google bot, since they block it. With WordpPress.com still I can export my content anytime in case I want a custom installation on a server of mine, while I&#8217;m locked-in with Contentful.

### Netlify

I was blown away by [Netlify][5]&#8216;s ease of use. It allows me to connect my Github repository to Netlify, runs the build process when I push to master, and automatically redirects all requests to /index.html. Wow.

### Conclusions

All in all, I&#8217;m currently very happy of my React / WordPress combo. It allows for fun development, great performances and simple deployments, while retaining the great publishing experience of WordPress and the no-nonsense [JAM stack][6] approach. Using WordPress also makes it easy to expand my blog with categories, tags, and plugins like Advanced Custom Fields in case I want to.
This is definitely the way I would go in case I had to do any &#8220;artisan&#8221; client work in 2019.

_Photo by [Thierry Meier][7] on [Unsplash][8]_

[1]: https://wordpress.org/support/plugin/static-html-output-plugin/reviews/
[2]: https://reach.tech/router
[3]: https://www.contentful.com
[4]: https://wordpress.org/
[5]: https://www.netlify.com/
[6]: https://jamstack.org/
[7]: https://unsplash.com/photos/PKEPAeMBOIU?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[8]: https://unsplash.com/search/photos/sea?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
