---
layout: layout.njk
title: Basic usage of the new React Router v6 (beta)
author: akmur
type: post
date: 2020-07-23T10:43:09+00:00
featured_image: https://vccw.test/wp-content/uploads/2020/07/bogdan-karlenko-36b7JBzhfF4-unsplash-scaled-e1595501218479.jpg
categories:
  - Articles
---

In this post we are going to look into how to use get started with the upcoming React Router version 6, currently in beta. Surely there are many more capabilities than those shown here, but this will get any app started, and might be enough for most of them.

### Installation

To get started, install these packages:

<pre><code class="language-javascript">npm install history react-router-dom@next react-router@next</code></pre>

This will install (at the time of writing) these package versions in your package.json:

<pre><code class="language-">"history": "^5.0.0",
"react-router": "^6.0.0-beta.0",
"react-router-dom": "^6.0.0-beta.0"</code></pre>

### The router component

For the sake of this example, we will create a few pages and we will see how to reach them, extract url parameters and search queries.

This is the code for my _AppRouter_ component, which you will likely import at some point within your application (for example, in the _App_ component)

Note: Your _Navigation_ component needs to exist inside the router.

<pre><code class="language-javascript">import React from 'react'
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom'

import Home from './pages/Home'
import About from './pages/About'
import Single from './pages/Single'
import FourOFour from './pages/FourOFour'
import Search from './pages/Search'
import Navigation from './ui/Navigation'

const AppRouter = () =&gt; {
  return (
    &lt;div className="AppRouter"&gt;
      &lt;Router&gt;
        &lt;Navigation /&gt;
        &lt;Routes&gt;
          &lt;Route element={&lt;Home /&gt;} path="/" /&gt;
          &lt;Route element={&lt;About /&gt;} path="/about" /&gt;
          &lt;Route element={&lt;Single /&gt;} path="/single/:id" /&gt;
          &lt;Route element={&lt;Search /&gt;} path="/search" /&gt;
          &lt;Route element={&lt;FourOFour /&gt;} path="/*" /&gt;
        &lt;/Routes&gt;
      &lt;/Router&gt;
    &lt;/div&gt;
  )
}

export default AppRouter
</code></pre>

### Links within the application

We will now use the _Navigation_ component to reach those pages we created:

Here is how it looks like. As you can see it uses the Link component provided by the router.

<pre><code class="language-javascript">import React from 'react'
import { Link } from 'react-router-dom'

const Navigation = () =&gt; {
  return (
    &lt;nav className="Navigation"&gt;
      &lt;Link className="Navigation__link" to="/"&gt;
        Home
      &lt;/Link&gt;

      &lt;Link className="Navigation__link" to="/about"&gt;
        About
      &lt;/Link&gt;
    &lt;/nav&gt;
  )
}

export default Navigation
</code></pre>

### How to use the URL parameters

In the Single page component, we can grab the URL parameter &#8220;id&#8221; and use it for whatever we need, like fetching some more data from some APIs.

<pre><code class="language-javascript">import React from 'react'
import { useParams } from 'react-router-dom'

const Single = () =&gt; {
  const { id } = useParams()

  return &lt;div&gt;{id}&lt;/div&gt;
}

export default Single
</code></pre>

### How to use the location or query parameters

We have created a _Search_ page which would show different search results according to search query parameters. In order to grab those parameters you do like this:

<pre><code class="language-javascript">import React from 'react'
import { useLocation } from 'react-router-dom'

const Search = () =&gt; {
  const location = useLocation()
  const locationSearch = location.search

  return &lt;div&gt;{locationSearch}&lt;/div&gt;
}

export default Search
</code></pre>

You can then use the _locationSearch_ variable to extract the single parameters

So, that&#8217;s it! Hopefully this gave you a good starting point to implement React Router V6 in your app.

&#8212;

<span>Photo by <a href="https://unsplash.com/@bogdan_karlenko?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Bogdan Karlenko</a> on <a href="https://unsplash.com/s/photos/routes?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></span>
