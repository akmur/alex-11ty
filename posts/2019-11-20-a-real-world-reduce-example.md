---
layout: single.njk
title: A real world reduce() example
author: akmur
type: post
date: 2019-11-20T08:32:28+00:00
featured_image: https://images.unsplash.com/photo-1491904768633-2b7e3e7fede5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=900&q=60
url: https://alexmuraro.me/posts/2019-11-20-a-real-world-reduce-example/
excerpt: A simple use case for Array.reduce().
tags:
  - Articles
  - JavaScript
---

For a long time I couldn't think of a way to use _reduce_ beyond the classic sum example (taken from [MDN][1])

```
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;
```

A few days ago, I found a way to make reduce() actually useful to me. I have been using it to create a new array out of an array of objects.

I had an array of complex objects, and I wanted to just get an array containing one of those properties, the name.

```
const people = [
  {
    id: 1,
    entries: [{name: 'Peach'}, {name: 'Mario'}]
  },
  {
    id: 2,
    entries: [{name: 'Bowser'}]
  }
]

const reducer = (acc, current) => {
  return [...acc, ...current.entries]
}

const names = people.reduce(reducer, [])

console.log(names) // [{name: 'Peach'}, {name: 'Mario'}, {name: 'Bowser'}]
```

Not sure why I never thought of this before, but better late than never, right?

[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce

---

<span>Photo by <a href="https://unsplash.com/@kaidi_guo?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Kaidi Guo</a> on <a href="https://unsplash.com/s/photos/mountains?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>
