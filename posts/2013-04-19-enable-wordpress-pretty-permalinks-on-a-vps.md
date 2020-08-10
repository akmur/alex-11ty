---
layout: single.njk
title: Enable WordPress pretty permalinks
author: akmur
type: post
date: 2013-04-19T00:14:10+00:00
excerpt: Pretty permalinks on your vrtual private server are driving you mad? No more!
original_post_id:
  - 151
tags:
  - Articles
  - WordPress
---

Scenario: You have a VPS, you have installed Apache, MySQL, PHP and WOrdpress, and you want to enable pretty permalinks.
If you're getting a 404 error when accessing your WordPress posts after having enabled pretty permalinks in the settings, then this is how to solve the issue (at least it worked for me).

Log in into your VPS server.

```
ssh username@IP-ADDRESS
```

then let's get to the sites-enabled folder

cd /etc/apache2/sites-enabled

Here there is a file called 000-default

using something like nano (a simple text editor) open this file

```
(sudo) nano 000-default
```

Use sudo if you're not logged in as root.

Now that the file is open, you'll see something like this:

```
DocumentRoot /var/www

Options FollowSymLinks
AllowOverride None

Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
Allow from all
```

What we need to do is to change those two "AllowOverride None" to "AllowOverride All".
Like so:

```
DocumentRoot /var/www

Options FollowSymLinks
AllowOverride All

Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
Allow from all
```

Once it's done, just restart your apache server

```
/etc/init.d/apache2 restart
```

And your pretty permalinks should be working now! Nice!
