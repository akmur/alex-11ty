---
layout: single.njk
title: Modifying WP API response to add previous and next post ID
author: akmur
type: post
featured_image: https://images.unsplash.com/46/iYvDeqVGRbebiQv2PIJi_DSC_8407.JPG?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=900&q=60
url: https://alexmuraro.me/posts/2016-07-12-modifying-wp-api-response-add-previous-next-post-id/
excerpt: I am pretty sure most people have at least heard about the mighty WordPress APIs. These APIs make it possible to create, modify and retrieve posts from our WordPress installations, although what we really want to do the most should be to using WordPress as an awesome backend to power cool applications. Think the possibilities...
tags:
  - Articles
  - WordPress
---

I am pretty sure most people have at least heard about the mighty WordPress APIs. These APIs make it possible to create, modify and retrieve posts from our WordPress installations, although what we really want to do the most should be to using WordPress as an awesome backend to power cool applications. Think the possibilities...

Playing around with the APIs, I found out that the single post endpoint doesn't show the previous and next post, which might be useful for pagination. Thankfully, it turned out to be quite simple to extend the APIs, so I have packaged this into a small plugin you can find below... it's really quite simple and goes to show the superpowers granted to us by the WP APIs. Also, it might serve as a good reference in case you're a bit lost starting out with working with the APIs. Have fun!

[github.com/akmur/add-prev-next-to-wp-api][1]

[1]: https://github.com/akmur/add-prev-next-to-wp-api

---

<span>Photo by <a href="https://unsplash.com/@tanvimalik?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Tanvi Malik</a> on <a href="https://unsplash.com/collections/866966/mountains?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>
