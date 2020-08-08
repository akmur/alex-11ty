---
layout: single.njk
title: How to use AJAX to call a function in WordPress
author: akmur
type: post
date: 2016-07-12T12:40:26+00:00
url: /posts/720/ajax-call-function-wordpress/
color_start_header:
  - rgba(23, 56, 102, 1)
color_start_footer:
  - rgba(219, 55, 57, 1)
color_end_header:
  - rgba(219, 55, 57, 1)
color_end_footer:
  - rgba(23, 56, 102, 1)
original_post_id:
  - 720
categories:
  - Articles
tags:
  - AJAX
  - JavaScript
---

This might be old stuff for many people out there and I know that most things can be accomplished with the amazing WP API, still I think it's good to have a simple example of using AJAX to call a WordPress function in one post. Here we go!

### Scenario:

You want to request some data from WordPress (e.g. the previous post ID), through an AJAX call.

### How to do this:

The way I solved this was to add a global variable in the header, so that the WordPress AJAX URL is exposed. Then I added a function in my theme's function.php file, which would do the actual work. Finally, in my JavaScript file it's just a matter of calling my function with AJAX. I can then use the result to do what I need.

### In header.php

```js
&lt;script&gt;
  var ajaxurl = "' . admin_url('admin-ajax.php') . '";
&lt;/script&gt;
</code>
</pre>

### In function.php

<pre><code class="language-php">
function get_prev_ajax_handler() {
  // this is how you get access to the database
  global $wpdb;
  // get the id value which has been posted
  $post_id = intval( $_POST['id'] );
  // Get a global post reference
  global $post;
  // Get the post object for the specified post
  $post = get_post( $post_id );
  // Echo the previous post ID
  echo get_previous_post()-&gt;ID;
  // close the connection
  wp_die();
}

add_action('wp_ajax_get_prev', 'get_prev_ajax_handler');
add_action( 'wp_ajax_nopriv_get_prev', 'get_prev_ajax_handler' );
</code>
</pre>

### In script.js

<pre><code class="language-php">
function getPrevPostId(id){
  var prevPostId;
  $.post( ajaxUrl, {
      action: "get_prev",
      id: id
    }, function(prevPostId) {
      console.log(prevPostId)
    });
}
</code>
</pre>
```
