---
layout: layout.njk
title: Enable WordPress pretty permalinks
author: akmur
type: post
date: 2013-04-19T00:14:10+00:00
excerpt: Pretty permalinks on your vrtual private server are driving you mad? No more!
original_post_id:
  - 151
categories:
  - Articles
tags:
  - apache
  - wordpress
---

Scenario: You have a VPS, you have installed Apache, MySQL, PHP and WOrdpress, and you want to enable pretty permalinks.
If you&#8217;re getting a 404 error when accessing your WordPress posts after having enabled &#8220;pretty permalinks&#8221; in the settings, then this is how to solve the issue (at least it worked for me).

Log in into your VPS server.

<pre>ssh username@IP-ADDRESS
</pre>

then let&#8217;s get to the sites-enabled folder

cd /etc/apache2/sites-enabled

Here there is a file called 000-default

using something like nano (a simple text editor) open this file

<pre>(sudo) nano 000-default
</pre>

Use sudo if you&#8217;re not logged in as root.

Now that the file is open, you&#8217;ll see something like this:

<pre>DocumentRoot /var/www

Options FollowSymLinks
AllowOverride None


Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
 Allow from all

</pre>

What we need to do is to change those two &#8220;AllowOverride None&#8221; to &#8220;AllowOverride All&#8221;.

Once it&#8217;s done, just restart your apache server

<pre>/etc/init.d/apache2 restart
</pre>

And your pretty permalinks should be working now! Nice!<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="http://www.topodin.com/consultant.php">интернет консультант</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="https://topodin.com/seo/post/klyuchevye-slova-pri-prodvizhenii-veb-sayta-ih-smysl-i-znachenie">комплексная реклама</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="https://topodin.com/seo/post/eksperiment-kak-kontekstnaya-reklama-povyshaet-prodazhi">контекстная реклама в москве</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://seomagik.com/50-kr-gratis-casino-room.php">spela casino på ipad</a>
</div>

<!--/54cd9b6444c531422760804-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://childssiattorney.com/100-kr-gratis-casino-2014.php">nettikasinot netent</a>
</div>

<!--/54cd9b6444c531422760804-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://325soldiercreekrd.info/alfa-bank-kreditnaya-karti-1.php">фсс открытие расчетного счета</a>
</div>

<!--/54cd9b6444c531422760804-->
