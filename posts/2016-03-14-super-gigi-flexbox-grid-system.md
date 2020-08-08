---
layout: layout.njk
title: Super GiGi Flexbox grid system
author: akmur
type: post
date: 2016-03-14T22:18:26+00:00
excerpt: "In this post I'm going to explain how to get started with Super GiGi, a Flexbox based grid system created by the people at Objectway and by Davide Di Pumpo in particular."
url: /posts/693/super-gigi-flexbox-grid-system/
color_start_header:
  - rgba(23, 56, 102, 1)
color_start_footer:
  - rgba(219, 55, 57, 1)
color_end_header:
  - rgba(219, 55, 57, 1)
color_end_footer:
  - rgba(23, 56, 102, 1)
headerbg:
  - 686
original_post_id:
  - 676
publicize_twitter_user:
  - akmur
categories:
  - Articles
---

Flexbox has been getting lots of attention lately, and rightly so, as it makes it possible to solve problems in unique and responsive ways.
You might want to take into consideration Flexbox-based layouts in case you are building a truly responsive web application and you want to take advantage of cool Flexbox properties like ordering, direction, wrapping, growing, etc.

In this post I&#8217;m going to explain how to get started with [Super GiGi][1], a Flexbox based grid system created by the people at [Objectway][2] and by <a href="https://twitter.com/MakhBeth" target="_blank">Davide Di Pumpo</a> in particular.

But first, here&#8217;s what Davide himself has to say about SuperGigi:

_&#8220;When you design a website, usually you will use some kind of grid system. There are a lot of frameworks on the old wide web that will help you accomplish this. Sometimes they use float, sometimes they use tables, but there are a few that are using Flexbox.
And if you know [Flexbox][3] you know two things about it: 1, It’s awesome and 2, it can be a pain to do general layout with._

*Yeah I know, Flexbox isn’t meant to be used to develop grid systems. For this you should use [CSS Grid][4]. But you know, nobody (but Internet Explorer °*°) supports this feature yet&#8230;\_

_So Super GiGi does exactly this. It will help you set up your own Flexbox grid system, carrying in all the tricks to achieve cross browser support (yes, even IE), solutions for the known [Flexbug][5], optimisation for performances, and a lot of helpers to build a “row -> columns” structure that will be easier to manage and to maintain._

_Super GiGi&#8217;s main purpose is to be compliant to the [separation of concerns][6]; the first impact can weird you out if you are used to a framework like Bootstrap or Foundation, but after a while (especially if you are used to Susy or similar) you will see the benefits of this choice.&#8221;_

Now we&#8217;re ready to start getting acquainted with Super GiGi!

### Learning more about Flexbox

In case you want to know more about Flexbox in general, I recommend checking out the following resources:

- [A guide to Flexbox on Css-tricks][3]
- [Flexbox.io by Wes Bos][7]
- [Zoe Gillenwater on Enhancing Responsiveness with Flexbox][8]
- [Flexbox Codepen Examples by Davide Di Pumpo][9]

### Getting Started

First things first, download the repository, or even better use bower or npm to install it.

In my case, I installed it with bower, like so:

<pre>bower install super-gigi -S
</pre>

Then be sure to import the main.scss file at the start of your manifest style.scss (the one you use to import all other scss files), like:

<pre>@import [path to super-gigi]/dist/main
</pre>

### Let&#8217;s get rolling

As you might have noticed, the documentation contains quite a bit of available configuration, but don&#8217;t let that scare you.
This is how you can get started real quick to get a feeling of how this works.

First of all, detect your outer container (aka a row) and the inner columns, then style them like:

<pre>.Container {
  @include grid-row(false); // set it to true if this is nested inside another container
}

.Container__header {
  @include grid-column(4);
}

.Container__main {
  @include grid-column(8);
}
</pre>

You will see that now your layout has got the familiar columns layout.

It is worth noting that the grid-row() mixin uses &#8220;flex-direction: row&#8221; property by default. In case you need boxes to stack vertically, you will need to use:

<pre>grid-row(false, true)
</pre>

where the first attribute is to determine if the container is nested (in this example it is not), and the second is used to determine the flex-direction.

Also worth mentioning is the fact that the grid-column(), which is the most important mixin in the whole library, takes a number of parameters which will speed up development time considerably. Here is an example taken straight from the docs:

<pre>.foo {
  @include grid-column(
      $width: (xxsmall:6, large: 6),
      $push: (xxsmall:6, large: 12),
      $pull: 1,
      $order: 0,
      $collapse: false,
      $global: true,
      $eq-grid: false
    );
};
</pre>

And an everyday use case:

<pre>.Column {
  @include grid-column($width: (small: 6, medium: 4, large: 3));
};
</pre>

### Changing basic settings

There is a wide number of settings that you might want to change to have Super GiGi work just like you need it, but before checking them out, let&#8217;s see how to overwrite the defaults.

First of all, if you wish (you know you do) to use Super GiGi&#8217;s utility functions, you should import Super GiGi&#8217;s \_functions.scss file before anything else.

So your manifest style.scss (where you keep all your imports) will look like this:

<pre>@import '../bower_components/super-gigi/dist/helpers/functions';
@import '[path-to-your-variable-file]/variables';
@import '../bower_components/super-gigi/dist/main';
</pre>

Now, to change the basic settings, you just need to write new variable values in your variables file. Something like:

<pre>$column-gutter: rem-calc(100);
$rem-base: 21px !default;
</pre>

One special mention for breakpoints. Those values are arranged in a \$breakpoints variable, which you can change if you wish, to something like the following.

<pre>$breakpoints: (
  xxsmall: 0em,
  small: em-calc(768),
  medium: em-calc(1024),
  large: em-calc(1400),
  xlarge: em-calc(1800)
);
</pre>

Hint: you can see all the default variables in the file:

<pre>@import [path to super-gigi]/dist/helpers/_variables.scss
</pre>

Remember that this grid is mobile first by default, but in case you need it to be &#8220;desktop first&#8221;, you can set this variable in your \_variables.scss file:

<pre>$query-direction: (max-width, min-width);
</pre>

### Functions

Super GiGi includes a number of useful functions as well, for example the **media-query** function. Just pass a breakpoint name to make it work.

<pre>@include media-query(medium) {
  // some rules
}
</pre>

We also have things like **rem-calc()** to calculate rem values starting from pixels, **dry-it()** to clean up your code, **hide-from()** and **show-from()** to hide or show starting from a certain breakpoint, and much more. You can find them all documented in the [repository][1].

### Conclusions

Lots of work and thinking went into Super Gigi, and you can tell. This is a powerful Sass library, and an absolute must if you need to deal with ultra-responsive Flexbox layouts.

You can follow <a href="https://twitter.com/MakhBeth" target="_blank">Davide Di Pumpo</a> on Twitter. Davide is also the author of the Super GiGi logo!

[1]: https://github.com/Objectway/super-gigi
[2]: http://www.objectway.com/
[3]: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
[4]: https://hacks.mozilla.org/2015/09/the-future-of-layout-with-css-grid-layouts/
[5]: https://github.com/philipwalton/flexbugs
[6]: https://www.w3.org/TR/html-design-principles/#separation-of-concerns
[7]: http://flexbox.io/
[8]: https://vimeo.com/124796320
[9]: http://codepen.io/MakhBeth/pen/avedNx
