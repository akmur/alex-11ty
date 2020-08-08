---
layout: layout.njk
title: A real world reduce() example
author: akmur
type: post
date: 2019-11-20T08:32:28+00:00
url: /posts/1447/a-real-world-reduce-example/
categories:
  - Articles
---

For a long time I couldn&#8217;t think of a way to use _reduce_ beyond the classic sum example (taken from [MDN][1])

<pre><code class="language-javascript">const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) =&gt;
  accumulator + currentValue;</code></pre>

A few days ago, I found a way to make reduce() actually useful to me. I have been using it to create a new array out of an array of objects.

I had an array of complex objects, and I wanted to just get an array containing one of those properties, the name.

<pre><code class="language-javascript">const people = [
  {
    id: 1,
    entries: [{name: 'Peach'}, {name: 'Mario'}]
  },
  {
    id: 2,
    entries: [{name: 'Bowser'}]
  }
]

const reducer = (acc, current) =&gt; {
  return [...acc, ...current.entries]
}

const names = people.reduce(reducer, [])

console.log(names) // [{name: 'Peach'}, {name: 'Mario'}, {name: 'Bowser'}]</code></pre>

Not sure why I never thought of this before, but better late than never, right?

[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce
