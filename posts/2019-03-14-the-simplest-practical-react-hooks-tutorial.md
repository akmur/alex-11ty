---
layout: single.njk
title: The simplest practical React Hooks tutorial
author: akmur
type: post
date: 2019-03-14T08:47:05+00:00
url: /posts/1318/the-simplest-practical-react-hooks-tutorial/
featured_image: https://vccw.test/wp-content/uploads/2019/03/christian-fregnan-269506-unsplash-e1552553186224.jpg
categories:
  - Articles
---

Since React hooks came out with React 16.8, I've seen many hooks tutorials popping up. They are surely interesting and I recommend them, but they can be sometimes a bit long and scary. In any case, as always I think it is beneficial to explain things with different words.

In a nutshell, React Hooks are used to add state and lifecycle to function components, which, prior to Hooks, could only be &#8220;dumb&#8221; and print whatever props they were passed from outer components.

In this post I want to show the simplest React Hooks example. It contains both **&#8220;useState&#8221;**, used make use of  state inside the component, and **&#8220;useEffect&#8221;**, used to run code when the component is loaded, or when props or state change.

So, here is my example, which is hopefully pretty self explanatory. (click on the coloured buttons to switch between editor and browser view)

What is happening?

On lines 6 and 7 we set two state variables we want to use (_showText_ and _text_), along with two actions used to update them (_setShowText_ and _setText_). We also set starting values for those two variables.
To be more precise, when we set:

<pre class="line-numbers language-javascript"><code class=" language-javascript">&lt;span class="token keyword"&gt;const&lt;/span&gt; &lt;span class="token punctuation"&gt;[&lt;/span&gt;text&lt;span class="token punctuation"&gt;,&lt;/span&gt; setText&lt;span class="token punctuation"&gt;]&lt;/span&gt; &lt;span class="token operator"&gt;=&lt;/span&gt; &lt;span class="token function"&gt;useState&lt;/span&gt;&lt;span class="token punctuation"&gt;(&lt;/span&gt;&lt;span class="token string"&gt;''&lt;/span&gt;&lt;span class="token punctuation"&gt;)&lt;/span&gt;</code></pre>

We are setting the variable &#8220;text&#8221; to a starting value of an empty string, and also setting up a &#8220;setText&#8221; function which we will be able to use to update the &#8220;text&#8221; variable later in the code.

On line 9, we have a _handleClick_ function. When it runs, it sets the _showText_ variable to the opposite of what it was, effectively toggling between a true and a false state.

On line 12, we have the useEffect function. As the [React docs][1] say, &#8220;you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined&#8221;. This means this _useEffect_ function will run when the component mounts, and everytime we update it by changing its props.

Then from line 18 to 21 we render the component.

Please note that useState and useEffect are only 2 of a number of available hooks (like useRef, useMemo, useDebugValue), although probably these are the most used. On [usehooks.com][2] you can find lots of info about hooks.

So that's it, there are the basics of React Hooks. If you would like to discuss it, you can do so on Linkedin:

<blockquote class="blockquote__linkedin data-lang=" style="border-color: #1D77B5;">
  <p dir="ltr" lang="en">
    I have written (hopefully) the simplest practical React Hooks tutorial
  </p>

  <p>
    — Alessandro Muraro &#8211; February 21, 2019
  </p>

  <p>
    <a href="https://www.linkedin.com/feed/update/urn:li:activity:6511886344573251584">Check it out on LinkedIn</a>
  </p>
</blockquote>

_Photo by [Christian Fregnan][3] on_ [_Unsplash_][4]

[1]: https://reactjs.org/docs/hooks-effect.html
[2]: https://usehooks.com/
[3]: https://unsplash.com/photos/f76zzdCEBgw?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://unsplash.com/search/photos/hook?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
