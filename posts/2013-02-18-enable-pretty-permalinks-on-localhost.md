---
layout: layouts/post.njk
title: Enable pretty permalinks on localhost
author: akmur
type: post
date: 2013-02-18T16:54:43+00:00
url: https://alexmuraro.me/posts/posts/2013-02-18-enable-pretty-permalinks-on-localhost/
excerpt: "Just a quick and simple tip. If you are on ubuntu and working with WordPress on a local installation, and you are finding yourself in the situation of being unable to access your posts when you enable pretty permalinks (which is, a custom post structure in Settings > Permalinks), the reason could be that you simply need to enable mod rewrite on you local Apache server."
tags:
  - WordPress
---

Just a quick and simple tip. If you are on ubuntu and working with WordPress on a local installation, and you are finding yourself in the situation of being unable to access your posts when you enable pretty permalinks (which is, a custom post structure in Settings > Permalinks), the reason could be that you simply need to enable mod rewrite on you local Apache server.

How to do it? Just open up your terminal and write:

```
sudo a2enmod rewrite
```

Followed by:

```
sudo service apache2 restart
```

Now everything should work!
