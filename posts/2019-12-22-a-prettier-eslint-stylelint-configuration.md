---
layout: single.njk
title: A Prettier / ESlint / stylelint configuration
author: akmur
type: post
date: 2019-12-22T00:34:54+00:00
tags:
  - Articles
---

[Prettier][1] is a tool that allows your code to be automatically formatted according to certain rules.

It is a great time saver, because you can paste your code in any way you like, and upon saving it will be prettified. This is especially valuable in a team environment. Prettier works with JavaScript files and Scss/CSS files, and it's even possible to automatically sort properties in Sass, by using stylelint and stylelint-order.

So I have created for my own reference a starter configuration that enables your projects to highlight errors and format code on save according to [Prettier][1] rules.

You will need the **Prettier**, **Eslint** and **stylelint** packages for VS Code.

You can find the code here: [github.com/akmur/react-prettier-setup][2]

[1]: https://prettier.io
[2]: https://github.com/akmur/react-prettier-setup
