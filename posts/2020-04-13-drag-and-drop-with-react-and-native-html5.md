---
layout: layouts/post.njk
title: Drag and drop with React and native HTML5
author: akmur
type: post
date: 2020-04-13T01:58:31+00:00
featured_image: https://images.unsplash.com/photo-1485160497022-3e09382fb310?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=60
url: https://alexmuraro.me/posts/2020-04-13-drag-and-drop-with-react-and-native-html5/
excerpt: "In this post I would like to show how you can implement a simple drag and drop features using the native HTML5 drag and drop events and React (but clearly you could use anything you like). I have seen a number of feature-packed libraries that surely accomplish everything you can dream of but this is how I you can get it done in the simplest way."
tags:
  - React
  - JavaScript
---

In this post I would like to show how you can implement a simple drag and drop features using the native HTML5 drag and drop events and React (but clearly you could use anything you like). I have seen a number of feature-packed libraries that surely accomplish everything you can dream of but this is how I you can get it done in the simplest way.

### Codesandbox

Here is the Codesandbox for this demo. For some reason the drag and drop feature seems to not be working inside this iframe, so maybe just open it in a new tab.

<iframe src="https://codesandbox.io/embed/basic-react-html5-drag-n-drop-fgy0c?fontsize=14&hidenavigation=1&theme=dark&view=editor"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="Basic React HTML5 Drag n Drop"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

### How does it work

In order to accomplish the drag and drop, we make use of a number of native events implemented in _Card.js_ and _Dropzone.js_. In **Card.js** you should pay attention to the following **handleDragStart** function, which is triggered when you start dragging. It will save some data using the native HTML5 method _dataTransfer.setData_.

```
const handleDragStart = e => {
  e.dataTransfer.effectAllowed = 'move'
  e.dataTransfer.setData('id', props.id)
}
```

In **Dropzone.js** you will find a series of functions that are triggered when entering, leaving, hovering a _dropzone_, plus the **handleDrop** function, triggered when releasing an element over the _dropzone_. When this happens, the following function is used to retrieve the saved data, set the dragging state to false, and call the function that will take care of changing the status of the card. Please note that props.status comes down from _App.js._

```
const handleDrop = e => {
  const id = parseInt(e.dataTransfer.getData('id'), 10)
  setIsDraggingOver(false)

  context.changeCardStatus(id, props.status)
}
```

**Warning**: I did not implement reordering of the cards, too much work 🙂 but I suppose something can be hacked together by using the APIs shown here, by getting the initial order and the order of the card you are dropping onto.

You can find the state of the app and the changeCardStatus function in **context.js.**
