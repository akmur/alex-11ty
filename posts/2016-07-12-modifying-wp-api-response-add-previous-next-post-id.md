---
layout: layout.njk
title: Modifying WP API response to add previous and next post ID
author: akmur
type: post
date: 2016-07-12T14:21:18+00:00
url: /posts/725/modifying-wp-api-response-add-previous-next-post-id/
color_start_header:
  - rgba(23, 56, 102, 1)
color_start_footer:
  - rgba(219, 55, 57, 1)
color_end_header:
  - rgba(219, 55, 57, 1)
color_end_footer:
  - rgba(23, 56, 102, 1)
original_post_id:
  - 725
publicize_twitter_user:
  - akmur
categories:
  - Articles
---

I am pretty sure most people have at least heard about the mighty WordPress APIs. These APIs make it possible to create, modify and retrieve posts from our WordPress installations, although what we really want to do the most should be to using WordPress as an awesome backend to power cool applications. Think the possibilities&#8230;

Playing around with the APIs, I found out that the single post endpoint doesn&#8217;t show the previous and next post, which might be useful for pagination. Thankfully, it turned out to be quite simple to extend the APIs, so I have packaged this into a small plugin you can find below&#8230; it&#8217;s really quite simple and goes to show the superpowers granted to us by the WP APIs. Also, it might serve as a good reference in case you&#8217;re a bit lost starting out with working with the APIs. Have fun!

[github.com/akmur/add-prev-next-to-wp-api][1]

[1]: https://github.com/akmur/add-prev-next-to-wp-api
