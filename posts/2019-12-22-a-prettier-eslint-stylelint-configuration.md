---
layout: layout.njk
title: A Prettier / ESlint / stylelint configuration
author: akmur
type: post
date: 2019-12-22T00:34:54+00:00
url: /posts/1516/a-prettier-eslint-stylelint-configuration/
categories:
  - Articles
---

[Prettier][1] is a tool that allows your code to be automatically formatted according to certain rules.

It is a great time saver, because you can paste your code in any way you like, and upon saving it will be prettified. This is especially valuable in a team environment. Prettier works with JavaScript files and Scss/CSS files, and it&#8217;s even possible to automatically sort properties in Sass, by using stylelint and stylelint-order.

This is the magic that happens when you save a file:

**Scss**

<img class="alignnone size-full wp-image-1518" src="https://vccw.test/wp-content/uploads/2019/12/Dec-22-2019-01-29-30.gif" alt="" width="430" height="150" />

**JavaScript**

<img class="alignnone size-full wp-image-1519" src="https://vccw.test/wp-content/uploads/2019/12/Dec-22-2019-01-32-32.gif" alt="" width="696" height="414" />

So I have created for my own reference a starter configuration that enables your projects to highlight errors and format code on save according to [Prettier][1] rules.

This is the content of the repository:

<img class="alignnone size-full wp-image-1517" src="https://vccw.test/wp-content/uploads/2019/12/Screenshot-2019-12-22-at-01.17.03.jpg" alt="" width="670" height="317" srcset="https://vccw.test/wp-content/uploads/2019/12/Screenshot-2019-12-22-at-01.17.03.jpg 670w, https://vccw.test/wp-content/uploads/2019/12/Screenshot-2019-12-22-at-01.17.03-300x142.jpg 300w" sizes="(max-width: 670px) 100vw, 670px" />

You will need the **Prettier**, **Eslint** and **stylelint** packages for VS Code.

You can find the code here: [github.com/akmur/react-prettier-setup][2]

[1]: https://prettier.io
[2]: https://github.com/akmur/react-prettier-setup
