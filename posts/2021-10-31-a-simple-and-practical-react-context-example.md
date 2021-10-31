---
layout: layouts/post.njk
title: "A simple and practical React context example"
type: post
date: 2021-10-31 11:11:00
url: https://alexmuraro.me/posts/2021-01-31-a-simple-and-practical-react-context-example
excerpt: "I couldn't find a simple enough React context example so I made one for future reference."
tags:
  - React
  - context
---

I couldn't find a simple enough React context example so I made one.
The meat of the example is in `UserContext.js`, which holds the state and changes it.
This state is then used in an inner component, `Details.js`

<iframe src="https://codesandbox.io/embed/react-context-example-flvtg?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="React context example"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
