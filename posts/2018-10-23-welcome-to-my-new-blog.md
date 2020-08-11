---
layout: single.njk
title: Welcome to my new blog
author: akmur
type: post
date: 2018-10-23T00:12:24+00:00
featured_image: /assets/images/pxem.jpg
url: https://alexmuraro.me/posts/2018-10-23-welcome-to-my-new-blog/
excerpt: Today I have launched my new blog. It is not simply a new theme (or actually, two themes, try out the "switch theme button" in the top right corner); it also has got an entirely new technical architecture to go with it.
tags:
  - Articles
---

Today I have launched my new blog. It is not simply a new theme (or actually, two themes, try out the "switch theme button" in the top right corner); it also has got an entirely new technical architecture to go with it.

But first, I want to take the chance to go through all the designs I did for this site over the years, with a little help from the Wayback Machine. Unfortunately some iterations have been lost, but it is still fun to look at:

[2012 Theme (using a different domain)][1]

<img src="/assets/images/acmpxm5.jpg" />

[2014 Theme][3]

<img src="/assets/images/gud0m6b.jpg" />

[2015 Theme][5]

<img src="/assets/images/pjxin1o.png" />

[2017 Theme][7]

<img src="/assets/images/srr08yn.png" />

Talking about the technological side, the site has been powered by WordPress for years, until early 2018 when I switched it to a static site, still generated from WordPress.

So, this morning I am deploying the version of the site you can see now. It is a purely frontend website, with its content pulled from [Contentful][9]. I have decided not to use any frontend framework after having played around with React, Preact, React router, and Next.js. It was fun to implement my site with different tools, and I learnt a lot during the process, but in the end I decided all that stuff was overkill, and went with vanilla JavaScript. The only JavaScript library I use is [Navigo.js][10] for routing.

I feel really happy with the result, I like the new design and the site is super fast. Plus, I can create new posts just by creating new markdown files. Google can even index JavaScript rendered pages, so what's not to love? 🙂

UPDATE 2019: I'm back to using WordPress, which then generates a static website. I love the usability of the admin area, cannot live without it!

UPDATE 2020: I've switched to Eleventy :)

[1]: https://web.archive.org/web/20120114220703/http://inteoria.net/
[2]: https://muraro.xyz/wp/wp-content/uploads/2019/02/acmpxm5.jpg
[3]: https://web.archive.org/web/20140802152258/http://vccw.test/
[4]: https://muraro.xyz/wp/wp-content/uploads/2019/02/gud0m6b.jpg
[5]: https://web.archive.org/web/20150511110509/http://vccw.test:80/
[6]: https://muraro.xyz/wp/wp-content/uploads/2019/02/pjxin1o.png
[7]: https://web.archive.org/web/20170928062210/https://vccw.test/
[8]: https://muraro.xyz/wp/wp-content/uploads/2019/02/srr08yn.png
[9]: https://www.contentful.com/ "Contentful"
[10]: https://github.com/krasimir/navigo
