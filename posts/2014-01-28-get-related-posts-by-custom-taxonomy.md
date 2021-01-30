---
layout: layouts/post.njk
title: Get related posts by custom taxonomy
author: akmur
type: post
date: 2014-01-28T23:56:21+00:00
excerpt: "This is one great Wordpress snippet, wortyh of being safely saved on my blog."
url: https://alexmuraro.me/posts/2014-01-28-get-related-posts-by-custom-taxonomy
tags:
  - WordPress
---

In this post we're going to use [wp_query][1] and [custom taxonomies][2]. Let the fun begin!

What we want is to retrieve posts related to the one we are currently displaying through one (or more) custom taxonomy term by using the following snippet to retrieve the current post type and use it in creative ways. In my case, since I was out of creativity, I just chose to run a simpler query whenever the post_type is not "event. Check it out.

```
post_type = get_post_type();

if ($post_type == 'event'){
  $args = array(
    'post_type' => 'post',
    'posts_per_page' => '3',
    'tax_query' => array(
    'relation' => 'AND',
        array(
        'taxonomy' => 'shtags',
        'field' => 'slug',
        'terms' => $myterm,
        'operator' => 'IN'
        )
    )
  $my_posts = new WP_Query($args);
} else {
    $args = array(
    'post_type' => 'post',
    'posts_per_page'  => '1'
    );
  $my_posts = new WP_Query($args);
}
```

Credits go mainly to [Smashing Magazine][3] and hours of Googling in order to search for an easy solution.

[1]: http://codex.wordpress.org/Class_Reference/WP_Query
[2]: http://codex.wordpress.org/Function_Reference/register_taxonomy
[3]: http://wp.smashingmagazine.com/2013/01/14/using-wp_query-wordpress/
