---
layout: single.njk
title: How to use AJAX to call a function in WordPress
author: akmur
type: post
featured_image: https://images.unsplash.com/photo-1425136738262-212551713a58?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjI0MX0&auto=format&fit=crop&w=900&q=60
url: https://alexmuraro.me/posts/2016-07-12-ajax-call-function-wordpress/
excerpt: This might be old stuff for many people out there and I know that most things can be accomplished with the amazing WP API, still I think it's good to have a simple example of using AJAX to call a WordPress function in one post. Here we go!
tags:
  - Articles
  - JavaScript
  - WordPress
---

This might be old stuff for many people out there and I know that most things can be accomplished with the amazing WP API, still I think it's good to have a simple example of using AJAX to call a WordPress function in one post. Here we go!

### Scenario:

You want to request some data from WordPress (e.g. the previous post ID), through an AJAX call.

### How to do this:

The way I solved this was to add a global variable in the header, so that the WordPress AJAX URL is exposed. Then I added a function in my theme's function.php file, which would do the actual work. Finally, in my JavaScript file it's just a matter of calling my function with AJAX. I can then use the result to do what I need.

### In header.php

```
<script>
  var ajaxurl = "' . admin_url('admin-ajax.php') . '";
</script>
```

### In function.php

```
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
  echo get_previous_post()->ID;
  // close the connection
  wp_die();
}

add_action('wp_ajax_get_prev', 'get_prev_ajax_handler');
add_action( 'wp_ajax_nopriv_get_prev', 'get_prev_ajax_handler' );
```

### In script.js

```
function getPrevPostId(id){
  var prevPostId;
  $.post( ajaxUrl, {
      action: "get_prev",
      id: id
    }, function(prevPostId) {
      console.log(prevPostId)
    });
}
```

---

<span>Photo by <a href="https://unsplash.com/@roylandnye?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Lee Roylland</a> on <a href="https://unsplash.com/s/photos/mountains?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>
