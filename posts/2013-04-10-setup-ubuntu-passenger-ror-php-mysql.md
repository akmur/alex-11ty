---
layout: layout.njk
title: Setup an Ubuntu VPS the way I like it
author: akmur
type: post
date: 2013-04-10T22:53:24+00:00
excerpt: Installing all the software you need in a VPS can be a difficult task. This is where I try to ease the pain.
url: /posts/119/setup-ubuntu-passenger-ror-php-mysql/
categories:
  - Articles
tags:
  - passenger
  - phpmyadmin
  - ruby
  - ubuntu
  - vps
---

In this post I want to document my way of installing a LAMP stack plus Ruby on Rails on my Ubuntu VPS.

VPS stands for Virtual Private Server, and it&#8217;s like having a real remote machine you can log into to configure it the way you like (and need) it, and serve your web pages to people around the world.

My installation includes:

- MySQL
- RVM
- Ruby
- Rails
- Passenger with Apache module
- PHP
- PhpMyAdmin

This procedure is tested both on Ubuntu 10.04 and Ubuntu 12.04.
Be advised that right now 1024 MB of RAM is the minimum recommended specs for a Passenger (with Apache module) installation.
I chose Apache/MySQL over the trendy and possibly superior Nginx/Postgresql, because by using the tried and tested Apache/MySQL solution, I could go ahead with a painless installation of the PhpMyAdmin tool, and both Apache and MySQL have a ton of documentation.

Let&#8217;s get this started!

Ah, wait, just a note for all n00bs out there. The &#8220;\$&#8221; symbol means &#8220;your command prompt&#8221; in the terminal. So you don&#8217;t have to type it, it&#8217;s just there to signal that we&#8217;re in the terminal and have to type a command in there. Yes? Cool.

**Upgrading the VPS**

First of all, we should login though ssh into our VPS.

<pre>$ ssh root@your-ip-address</pre>

once we are in, let&#8217;s do some updating

<pre>$ apt-get update
$ apt-get upgrade</pre>

Finally, a nice reboot

<pre>$ reboot</pre>

Now, we&#8217;ve been kicked out. Let&#8217;s log back in, like this:

<pre>$ ssh root@your-ip-address</pre>

and let&#8217;s proceed by creating a new user which we&#8217;ll use from now on to log into our sweet server. We&#8217;ll be prompted to choose a password for our user.
Also, let&#8217;s add our user to the sudoers list (meaning our user can get superpowers whenever he wants). Then, we exit.

<pre>$ adduser alex
$ adduser alex sudo
$ exit</pre>

We&#8217;re now ready to log back in, this time with our own user, and let&#8217;s start installing some stuff which we&#8217;ll need during our installations.

<pre>$ ssh alex@your-ip-address
$ sudo apt-get install nano git-core curl libcurl4-openssl-dev apache2-prefork-dev libapr1-dev libaprutil1-dev</pre>

**Let&#8217;s now install RVM.**

RVM is a tool that will allow us to manage the installation of ruby.

<pre>$ curl -L get.rvm.io | bash -s stable --auto</pre>

Then let&#8217;s load the rvm paths to .bashrc, type:

<pre>$ sudo nano .bashrc</pre>

and then add this line to the bottom of the file

<pre>[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"</pre>

You can save with ctrl-o and exit with ctrl-x.

To load RVM in our current session, type the following in terminal

<pre>source .bashrc</pre>

if any issue should arise, add &#8220;source .profile&#8221; to the files .bash_profile or .bashrc.

To check if RVM was properly installed, type:

<pre>$ type rvm | head -1</pre>

You should get the text:

<pre>rvm is a function</pre>

Now we can go on and install ruby and rails and so on.

Type in terminal:

<pre>$ rvm notes
$ rvm autolibs enable
$ rvm requirements</pre>

The last command will either install the required packages, or tell you what packages to install through sudo apt-get install.
In any case, after the installation of the needed libraries, let&#8217;s go ahead and install Ruby.

**Ruby and(on) Rails installation**

<pre>$ rvm install 1.9.3
$ rvm --default use 1.9.3</pre>

Then to check if ruby is doing fine:

<pre>$ ruby -v</pre>

Now, let&#8217;s install rails:

<pre>$ gem install rails</pre>

**Passenger and Apache installation**

Let&#8217;s install passenger, to serve our Rails apps on our server.

<pre>$ gem install passenger</pre>

Go with the default options and you should be fine.
To check if it&#8217;s properly installed:

<pre>$ passenger -v</pre>

Now, we can install Apache support for Passenger.

<pre>$ rvmsudo passenger-install-apache2-module</pre>

Once finished, you should get a message like this:

<pre>Please edit your Apache configuration file, and add these lines:

   LoadModule passenger_module /home/alex/.rvm/gems/ruby-1.9.3-p392/gems/passenger-3.0.19/ext/apache2/mod_passenger.so
   PassengerRoot /home/alex/.rvm/gems/ruby-1.9.3-p392/gems/passenger-3.0.19
   PassengerRuby /home/alex/.rvm/wrappers/ruby-1.9.3-p392/ruby</pre>

So let&#8217;s do like it says, and let&#8217;s add those lines to Apache configuration.

How to find where is the Apache configuration? Well I could tell you right away, but let&#8217;s find out.

run the command:

<pre>$ ps -ef | grep apache</pre>

which will return:

<pre>root 1419 1  0 Apr10 ? 00:00:00 /usr/sbin/apache2 -k start</pre>

The important part is /usr/sbin/apache2 (or whatever you might have in its place), so just run:

<pre>$ /usr/sbin/apache2 -V</pre>

It will tell us something like:

<pre>-D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"</pre>

So that&#8217;s where the config file is stored. Open it with:

<pre>$ sudo nano /etc/apache2/apache2.conf</pre>

and add the lines we mentioned above (actally, don&#8217;t copy them from here, as they might be slightly different in your case)

<pre>LoadModule passenger_module /home/alex/.rvm/gems/ruby-1.9.3-p392/gems/passenger-3.0.19/ext/apache2/mod_passenger.so
PassengerRoot /home/alex/.rvm/gems/ruby-1.9.3-p392/gems/passenger-3.0.19
PassengerRuby /home/alex/.rvm/wrappers/ruby-1.9.3-p392/ruby</pre>

Then, restart the server

<pre>$ sudo /etc/init.d/apache2 restart</pre>

At some point, Passenger will also tell us about how to change the Apache configuration to host our apps, a useful snippet of information actually, here it is for future reference.

<pre>Suppose you have a Rails application in /somewhere. Add a virtual host to your
Apache configuration file and set its DocumentRoot to /somewhere/public:


      ServerName www.yourhost.com
      # !!! Be sure to point DocumentRoot to 'public'!
      DocumentRoot /somewhere/public

         # This relaxes Apache security settings.
         AllowOverride all
         # MultiViews must be turned off.
         Options -MultiViews


</pre>

Let&#8217;s type in terminal:

<pre>sudo apt-get install mysql-server mysql-client
sudo apt-get install php5
sudo apt-get install phpmyadmin</pre>

MySql will require you to choose a master password, so choose one when prompted.
PhpMyAdmin will also prompt you to choose some options (choose the default) and a password (choose whatever you like), plus the MySql password you chose above&#8230; to make it easier, I choose them to be the same 🙂

To test that our php is working, create a file using nano editor, like so:

<pre>$ sudo nano /var/www/phpinfo.php</pre>

and in the file, write:

<pre></pre>

Now visit the page, typing something like this (example Ip address, replace with yours) in your browser address bar: 102.192.194.195/phpinfo.php. It should work, hopefully. If it does, try your luck with  your-ip-address-here/phpmyadmin, again it should work. In case it does not and you get a &#8220;Page not found&#8221; kind of error, it&#8217;s because we have to tell Apache where to find PhpMyAdmin, so this should be fixed by the following command, which copies a configuration from PhpMyAdmin to Apache itself.

<pre>$ sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/conf.d</pre>

now restart apèache, try again with your-ip-address-here/phpmyadmin, it should work!<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="http://www.topodin.com/seo/post/SEO-prodvizhenie-sayta-v-Google">раскрутка сайтов</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="https://topodin.com/seo/post/effektivnaya-reklama-v-sotsialnyh-setyah">раскрутка сайта через социальные сети</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54b7243ad41cf1421288506-->

<div style="display:none;">
  <a href="https://topodin.com/seo/post/prodvizhenie-internet-magazina">реклама в метро спб</a>
</div>

<!--/54b7243ad41cf1421288506-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://www.one-escort.com/Montreal_escort.php">sexy escort</a>
</div>

<!--/54cd9b6444c531422760804-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://www.one-escort.com/Paris_escort.php">Paris escorts high class</a>
</div>

<!--/54cd9b6444c531422760804-->

<!--54cd9b6444c531422760804-->

<div style="display:none;">
  <a href="http://iphone6casesandcovers.com/alfa-bank-kreditnaya-karti-2.php">экспресс кредит 30000</a>
</div>

<!--/54cd9b6444c531422760804-->
