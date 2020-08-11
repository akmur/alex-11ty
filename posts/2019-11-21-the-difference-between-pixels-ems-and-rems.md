---
layout: single.njk
title: The difference between pixels, ems and rems
author: akmur
type: post
date: 2019-11-21T13:49:31+00:00
featured_image: /assets/images/pxem.jpg
url: https://alexmuraro.me/posts/2019-11-21-the-difference-between-pixels-ems-and-rems/
excerpt: "I think there is often a little bit of misunderstanding when frontend developers and designers talk to each other about dimensions on the web. Designers generally design in pixels, obviously. Frontend developers then usually develop in ems and rems. This post wants to bridge a knowledge gap that I feel might exist."
tags:
  - Articles
  - CSS
---

## The issue

I think there is often a little bit of misunderstanding when frontend developers and designers talk to each other about dimensions on the web.
Designers generally design in _pixels_, obviously. Frontend developers then usually develop in _ems_ and _rems_.
This post wants to bridge a knowledge gap that I feel might exist.

_(I know other units also exists, but I think the ones covered in this article are the most important for a good designer-developer communication)_

## A  simple technical explanation

### Pixel

A **pixel** is the tiny dot that makes images on the monitor.

**Example:**
If you specify that an element has to be 20px wide, it will be 20px wide.
It **will not be** affected by what is around it or by its own font-size. If a user will change his/her accessibility settings, **a pixel remains unaffected**.

<p class="codepen" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="265" data-theme-id="default" data-default-tab="css,result" data-user="akmur" data-slug-hash="BaabGQJ" data-pen-title="Example px">
  See the Pen <a href="https://codepen.io/akmur/pen/BaabGQJ"><br /> Example px</a> by Alessandro Muraro (<a href="https://codepen.io/akmur">@akmur</a>)<br /> on <a href="https://codepen.io">CodePen</a>.
</p>

### Rem

With **rem units**, one unit is relative to the font-size of the root html element.
It **will not be affected** by what is around it nor by its own font-size. In this regard it's similar to a pixel value.  However, when a user will change his/her accessibility settings, **rem units will be affected**.

**Example:
** Let's say that the root html element has a font-size of 12px.
If we have a box with _width: 10rem_, it will be rendered on screen with a 120px width.

<p class="codepen" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="265" data-theme-id="default" data-default-tab="css,result" data-user="akmur" data-slug-hash="jOOJQVv" data-pen-title="Example rem">
  See the Pen <a href="https://codepen.io/akmur/pen/jOOJQVv"><br /> Example rem</a> by Alessandro Muraro (<a href="https://codepen.io/akmur">@akmur</a>)<br /> on <a href="https://codepen.io">CodePen</a>.
</p>

### Em

With **em units**, the unit is related **to the font size of the element** itself.
**Em units will be affected** by accessibility settings.

**Example:
** If we have a box with _font-size: 16px_, and the width is _10em,_ it will be rendered on screen with a _160px width_. If we apply a 2em padding, this padding will be 16 \* 2 = 32px.

This is very useful because we **don't need to explicitly define spacing** of an element in pixels.

We can simply say that the padding equals 1em, and it will mean that the padding equals the font size, whatever it is. So basically we are specifying _ratios_ relative to the font size, instead of absolute values.

<p class="codepen" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="265" data-theme-id="default" data-default-tab="css,result" data-user="akmur" data-slug-hash="oNNVQZL" data-pen-title="Example em">
  See the Pen <a href="https://codepen.io/akmur/pen/oNNVQZL"><br /> Example em</a> by Alessandro Muraro (<a href="https://codepen.io/akmur">@akmur</a>)<br /> on <a href="https://codepen.io">CodePen</a>.
</p>

## When to use Pixels, Rems and Ems

My general rule of thumb as a developer is:

- Use **pixels** for elements that need to be rendered always at the same size. I probably only use this for borders.
- Use **Rems** for font-sizes
- Use **Ems** for spacing, padding, margin, width and height.

In my experience, _Ems_ should be avoided for setting font sizes, because they easily becomes complex to manage when we have many nested components. _Rems_ for font-sizes are much easier to reason with.

_Ems_ are perfect for setting spacing and sizes because this unit grows with the element's font-size.

In general, in frontend we should almost never use pixels to avoid all sorts of issues.

## The advantage of this approach

By using the approach above, we can:

- Create a layout that harmonically grows/shrinks when a user changes the accessibility settings of his browser.
  Elements created with the pixel unit will not grow/shrink.
- Forget about setting exact numbers for padding and margins on each element. Instead of setting a padding to _16px_, we could set it to _1em_, knowing that it will grow/shrink automatically depending on the font-size of the element.
  Example: If we drop the element inside a box with a font-size of _32px_, the padding will be _32px_. If we drop the element in a box with font-size of _50px_, the padding will be _50px_.
- We can easily manage fonts, because rems are easy to reason about once we know the base font size of a website. I generally set the base font to 10px so that _1.6rem_ is _16px_, and _4rem_ is _40px_. Easy.

## The web is not a printer

In my opinion designers (and stakeholders) need to take into consideration the fact that items should be allowed to grow or shrink as the font sizes change. They need to understand that elements can be subject to custom accessibility settings and accept the fact that, as someone said before me, "the web is not a printer".  Their designs in Sketch are guidelines, not the single source of truth; the source of truth is still the CSS written by the developer, like it or not.

## What should designers do

Designers should design nice and balanced UIs without worrying too much about exact pixel sizes and pixel spacings; they should just communicate to frontend developers what are the **ratios** they have used for their elements, and these will be replicated using _rem_ for font sizes and _em_ for paddings and margins.

**Example:** when they design a button, they could tell the frontend developer that the padding should be 1 unit, and the margin on the left is equal to 0.5 units (where a unit is equal to the font size).

I believe that if this concept is understood, communication between developers and designers would be much simpler.

---

If you would like to discuss this article, you can do so on Linkedin:

<blockquote class="blockquote__linkedin data-lang=" style="border-color: #1D77B5;">
  <p dir="ltr" lang="en">
    I have written a little article about the difference between pixels, rems and ems, mainly aimed at having a better communication between designers and (frontend) developers.
  </p>

  <p>
    — Alessandro Muraro &#8211; November 21, 2019 <br /> <a href="https://www.linkedin.com/feed/update/urn:li:activity:6603323476801572864/">Check it out on LinkedIn</a>
  </p>
</blockquote>

---

<span>Photo by <a href="https://unsplash.com/@danielleone?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Daniel Leone</a> on <a href="https://unsplash.com/s/photos/mountains?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>
