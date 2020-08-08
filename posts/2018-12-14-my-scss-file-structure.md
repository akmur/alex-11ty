---
layout: single.njk
title: My SCSS file structure
author: akmur
type: post
date: 2018-12-14T00:14:58+00:00
url: /posts/1223/my-scss-file-structure/
timeline_notification:
  - 1549152953
categories:
  - Articles
---

After having created folder structures for my SCSS files many times for many different projects over the years, I decided to create a Github repository so that it's easier for me to get started and improve; hopefully it can be useful to somebody else trying to wrap his/her head around it as well.

First of all, [here is the repository][1] that you can clone to get started, and here below is an image that shows how the folder structure looks like.

[<img class="alignnone size-medium wp-image-1224" src="https://muraro.xyz/wp/wp-content/uploads/2019/02/3pm3of9.png?w=300" alt="" width="300" height="264" srcset="https://vccw.test/wp-content/uploads/2019/02/3pm3of9.png 337w, https://vccw.test/wp-content/uploads/2019/02/3pm3of9-300x264.png 300w" sizes="(max-width: 300px) 100vw, 300px" />][2]

The main ideas behind the organization of these files come from a couple of resources with a few tweaks, and 99% of the credit goes to them of course.

- [SASS Guidelines: 7-in-1 pattern][3]
- [ITCSS: Scalable and maintainable Scss architecture][4]

I am basically merging the two approaches, in order to have something that makes a lot of sense yet is easier to understand than the resources above. During the years I always found that the first approach was great but could have done with a bit more modularity, while the second one is a bit too technical to wrap one's head around.

So these are my folders:

### 01-Abstracts

Here you can find mixins, extends, placeholders and variables and all that code that doesn't actually outputs CSS.

### 02-Base

In this folder you can put generic reset styles like normalize.css, starters like Bootstrap or Bulma, typographic starters, stuff like fontawesome, and so on.

### 03-Elements

This folder contains styling for simple basic elements like buttons, links, titles, inputs. These are &#8220;units&#8221;. If more elements are merged, they go into the next folder.

### 04-Components

UI components are composed of elements. This means these components made up of elements. An example of a component is a group of buttons, a form, a header. This is where majority of our work takes place.

### 05-Pages

This folder contains code specific to certain pages. For example, some custom styling for the layout of the customer account.

### 06-Utilities

Utilities are very specific classes used to change appearance of some element. They should be prefixed with &#8220;u&#8221;. For example, .u-center could be used to center some text, u-uppercase to make it uppercase, u-floatLeft to float some image on the left, and so on.

### 07-Print

This folder contains print specific CSS.

### 77-Vendors

Here you can add third party code for plugins like slideshows, for example, while Bootstrap would go in the &#8220;02-Base&#8221; folder because it acts like a reset.

### 88-Legacy

This folder contains code for older browsers.

### 99-Overrides

Overrides for any of the folders above go here, however this is mainly for plugins. It should not be abused.

So far this file organization has proved to be quite good, easy to understand yet complex enough to allow for enough flexibility. Let me know if you have ideas for improvements.

[1]: https://github.com/akmur/scss-structure "Scss Structure Github Repo"
[2]: https://muraro.xyz/wp/wp-content/uploads/2019/02/3pm3of9.png
[3]: https://sass-guidelin.es/#the-7-1-pattern
[4]: https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/
