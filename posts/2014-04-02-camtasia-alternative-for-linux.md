---
layout: single.njk
title: Camtasia alternative for Linux
author: akmur
type: post
date: 2014-04-02T18:19:35+00:00
excerpt: Is there an alternative to Camtasia for Ubuntu?
tags:
  - Articles
  - Camtasia
  - Screencast
  - Linux
---

Camtasia (you can find it [here][1]) is a cool software for Mac and Windows, used to record your screen while simultaneously record your webcam stream.

It is very useful for screencasts, to give them more of a personal touch, or in case you need to record how people behave while testing out your website or application.

It a can be a fundamental tool, but what if you're on Ubuntu Linux? What's the alternative?

Well, we need to use two softwares. One is [Kazam][2] available from the Ubuntu Software Centre. This is a complete screencasting tool, which you need to set like in the following image:

<img class="alignnone size-full wp-image-819" src="/images/camtasia-post-screen-1.jpeg" alt="kazam-screencaster_009" />

&nbsp;

Please note that you have to activate and set the audio source as "Built in Analog Stereo" (or whatever your input) so that you can record audio too.

Now, for the webcam bit, I found the best option to be [GUVC View][3], also available in the Software Center. Once installled it, it should open up. Go to the settings, and just to be sure disable the audio input.

<img class="alignnone size-full wp-image-820" src="/images/kazam-screencaster_0091.jpeg" />

You should see your nice mug now, on a second window. What you want to do is to tell this window to always be on top, like so:

<img class="alignnone size-full wp-image-821" src="/images/selection_015.jpeg" alt="selection_015" />

Now you can move this window in the proper position on your screen, and start recording your screencast using Kazam. Before starting, you might want to select the encoder type (MP4 or WebM) and select the region to be recorded through the button _Record Region_ so that you don't end up recording unnecessary screen regions.

<img class="alignnone size-full wp-image-822" src="/images/kazam-screencaster_00911.jpeg" alt="Kazam-Screencaster_0091.jpeg" />

[1]: http://www.techsmith.com/camtasia.html
[2]: https://apps.ubuntu.com/cat/applications/precise/kazam/
[3]: https://apps.ubuntu.com/cat/applications/guvcview/
