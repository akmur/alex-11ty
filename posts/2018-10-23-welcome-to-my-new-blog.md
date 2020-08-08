---
layout: single.njk
title: Welcome to my new blog
author: akmur
type: post
date: 2018-10-23T00:12:24+00:00
url: /posts/1217/welcome-to-my-new-blog/
timeline_notification:
  - 1549152883
categories:
  - Articles
---

Today I have launched my new blog. It is not simply a new theme (or actually, two themes, try out the &#8220;switch theme button&#8221; in the top right corner); it also has got an entirely new technical architecture to go with it.

But first, I want to take the chance to go through all the designs I did for this site over the years, with a little help from the Wayback Machine. Unfortunately some iterations have been lost, but it is still fun to look at:

[2012 Theme (using a different domain)][1]

[<img class="alignnone wp-image-1218 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2019/02/acmpxm5.jpg?w=700" alt="" width="700" height="383" srcset="https://vccw.test/wp-content/uploads/2019/02/acmpxm5.jpg 2880w, https://vccw.test/wp-content/uploads/2019/02/acmpxm5-300x164.jpg 300w, https://vccw.test/wp-content/uploads/2019/02/acmpxm5-768x420.jpg 768w, https://vccw.test/wp-content/uploads/2019/02/acmpxm5-1024x560.jpg 1024w, https://vccw.test/wp-content/uploads/2019/02/acmpxm5-1568x857.jpg 1568w" sizes="(max-width: 700px) 100vw, 700px" />][2]

[2014 Theme][3]

[<img class="alignnone wp-image-1219 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2019/02/gud0m6b.jpg?w=700" alt="" width="700" height="384" srcset="https://vccw.test/wp-content/uploads/2019/02/gud0m6b.jpg 2838w, https://vccw.test/wp-content/uploads/2019/02/gud0m6b-300x165.jpg 300w, https://vccw.test/wp-content/uploads/2019/02/gud0m6b-768x422.jpg 768w, https://vccw.test/wp-content/uploads/2019/02/gud0m6b-1024x562.jpg 1024w, https://vccw.test/wp-content/uploads/2019/02/gud0m6b-1568x861.jpg 1568w" sizes="(max-width: 700px) 100vw, 700px" />][4]

[2015 Theme][5]

[<img class="alignnone wp-image-1220 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2019/02/pjxin1o.png?w=700" alt="" width="700" height="386" srcset="https://vccw.test/wp-content/uploads/2019/02/pjxin1o.png 2834w, https://vccw.test/wp-content/uploads/2019/02/pjxin1o-300x165.png 300w, https://vccw.test/wp-content/uploads/2019/02/pjxin1o-768x423.png 768w, https://vccw.test/wp-content/uploads/2019/02/pjxin1o-1024x564.png 1024w, https://vccw.test/wp-content/uploads/2019/02/pjxin1o-1568x864.png 1568w" sizes="(max-width: 700px) 100vw, 700px" />][6]

[2017 Theme][7]

[<img class="alignnone wp-image-1221 size-large" src="https://muraro.xyz/wp/wp-content/uploads/2019/02/srr08yn.png?w=700" alt="" width="700" height="372" srcset="https://vccw.test/wp-content/uploads/2019/02/srr08yn.png 2840w, https://vccw.test/wp-content/uploads/2019/02/srr08yn-300x159.png 300w, https://vccw.test/wp-content/uploads/2019/02/srr08yn-768x408.png 768w, https://vccw.test/wp-content/uploads/2019/02/srr08yn-1024x544.png 1024w, https://vccw.test/wp-content/uploads/2019/02/srr08yn-1568x833.png 1568w" sizes="(max-width: 700px) 100vw, 700px" />][8]

Talking about the technological side, the site has been powered by WordPress for years, until early 2018 when I switched it to a static site, still generated from WordPress.

So, this morning I am deploying the version of the site you can see now. It is a purely frontend website, with its content pulled from [Contentful][9]. I have decided not to use any frontend framework after having played around with React, Preact, React router, and Next.js. It was fun to implement my site with different tools, and I learnt a lot during the process, but in the end I decided all that stuff was overkill, and went with vanilla JavaScript. The only JavaScript library I use is [Navigo.js][10] for routing.

I feel really happy with the result, I like the new design and the site is super fast. Plus, I can create new posts just by creating new markdown files. Google can even index JavaScript rendered pages, so what's not to love? 🙂

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
