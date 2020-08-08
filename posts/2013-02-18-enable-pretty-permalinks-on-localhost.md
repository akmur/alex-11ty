---
layout: layout.njk
title: Enable pretty permalinks on localhost
author: akmur
type: post
date: 2013-02-18T16:54:43+00:00
excerpt: "Can't access your Wordpress posts on a local installation because of an irritating 404 error? Fix it!"
categories:
  - Articles
tags:
  - apache
  - localhost
  - wordpress
---

Just a quick and simple tip. If you are on ubuntu and working with WordPress on a local installation, and you are finding yourself in the situation of being unable to access your posts when you enable pretty permalinks (which is, a custom post structure in Settings > Permalinks), the reason could be that you simply need to enable mod rewrite on you local Apache server.

How to do it? Just open up your terminal and write:

<pre>sudo a2enmod rewrite</pre>

Followed by:

<pre>sudo service apache2 restart</pre>

Now everything should work!<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="https://topodin.com">topodin.com</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="http://www.topodin.com/soprovojdeniye.php">техническая поддержка и сопровождение сайта</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54b7243ad41cf1421288506-->

<a style="display:none;">translate english to polish</a><!--/54b7243ad41cf1421288506-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://formaldehyde-safety.com/avshori-chto-takoe.php">offshore company list</a>
</div>

<!--/54cd9b6444c531422760804-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://junkgeni.com/beliz-offshori.php">infinity group brisbane</a>
</div>

<!--/54cd9b6444c531422760804-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://www.one-escort.com/Paris_escort.php">Paris escorts reviews</a>
</div>

<!--/54cd9b6444c531422760804-->
