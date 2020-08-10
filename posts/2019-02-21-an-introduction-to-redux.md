---
layout: single.njk
title: An introduction to Redux
author: akmur
type: post
date: 2019-02-21T11:18:09+00:00
tags:
  - Tutorial
  - Redux
  - JavaScript
  - Article
---

Redux is a small popular library used to keep track of the state of an interface without going crazy. It is mainly used together with React, a popular library used to create snappy user interfaces on the web.

Getting started with redux might take a while, because you need to get accustomed to the way it does things. In this post i want to cut straight to the meat of the issue, without unnecessary technical explanations. I will show you how to get started with Redux in a React project.

### Why? {#why}

Why another tutorial about Redux? Because I finally grasped it after struggling with it for a while, and I have the feeling a new tutorial with new ways to explain the same concept might be helpful.

### Credits {#credits}

This tutorial would have not been possible without this one: [React Redux Tutorial for Beginners: The Definitive Guide][1] which I recommend as it's much more in depth than mine and very easy to follow.
Another great tutorial that helped me greatly is this one: [Understanding Redux — 1. – Ohans Emmanuel][2]
Also, once you have some understanding of Redux, I recommend checking out [Human Redux][3], it's really well written.

### Prerequisites {#prerequisites}

- node installed on your machine
- some basic react knowledge might help (so you don't feel completely lost)

## Cloning the project {#cloningtheproject}

Instead of copy-pasting stuff from a webpage, let's be modern and just clone or download this Git repository:

[GitHub &#8211; akmur/redux-tutorial: Redux Tutorial][4]

where you will find a little project already setup.

Once downloaded or cloned, open your Terminal and go to the project's folder, then type:

```
npm install
```

followed by:

```
npm run start
```

Now the application should be available at [localhost:3000][5].

## About the file structure {#aboutthefilestructure}

Inside the "src" folder, the main files you will find are the following React files:

```
./src
----User.js
----News.js
----Status.js
----index.js
```

And the following Redux files:

```
./src
----redux
--------actions
------------index.actions.js
--------middleware
------------index.middleware.js
--------reducers
------------user.reducers.js
------------news.reducers.js
------------index.reducers.js
------------status.reducers.js
--------store
------------index.js
```

## Redux 101 {#redux101}

The main concept behind Redux is that you have:

- Stores
- Actions
- Reducers
- Middlewares (optional)

Stores is where all the information about state is stored.
Actions is where we dictate what needs to happen in the form of a simple object.
Reducers are where the new state is updated with information coming from the actions.
Middlewares make it possible to intercept actions, and introduce secondary effects (like dispatching a new action or making an AJAX request).

## How does this work? {#howdoesthiswork}

I suppose we need some explanation, so we will be going through:

- [React index file][6]
- [React user component][7]
- [Redux action file][8]
- [Redux middleware][9]
- [Redux user reducer][10]
- [Redux store][11]

I will do my best to keep this short.

#### React index file {#react-index}

At the top of this files, you have all the imports needed to make it work. The last two imports are related to Redux.
We are importing the "Provider" component and the Redux store we already created.

The Provider will take our store as prop and wrap our application so that every component can easily be informed of the current status.

#### React User Component {#react-component}

Found in:
./src/User.js

At the top of the file, we have our standard imports needed to load React, load the "connect" feature from Redux, and load our Redux actions.

Inside the component, in the beginning of the component's lifecycle, inside the componentDidMount() function, we check if data is already loaded, and if not, we load it.

Inside the render() function we simply output the data.

Towards the end of the file, we have "const = mapStateToProps". Here we are mapping the user state saved in Redux, with the component's properties (props) so that they are available in the render() function.

In the last few lines, we are doing the actual plumbing, connecting everything together and exporting the component.

#### Redux Action {#redux-action}

Found in:
./src/redux/actions/index.actions.js

Then we have two functions, loadUser() and loadNews(). What they do is to basically return a simple object describing the action we want to perform. This action will be "intercepted" by the middleware, which in turn will take care of the AJAX requests.

#### Redux middleware {#redux-middleware}

Before we start, please note that I added some artificial delay to these Ajax requests, so the state change can be seen more easily.

Found in:
./src/redux/middleware/index.middleware.js

What this bit does is to intercept all actions and if, as an example, one called "LOAD USER" is found, it will dispatch a new action, in this case "USER_LOADED", togerther twith a payload, in this case the result of an AJAX call.

#### Redux User Reducer {#redux-reducer}

Found in:
./src/redux/reducers/user.reducers.js

This reducer, receives a state (the default if none other is available, is initialState) and an action.
If the reducer receives the action &#8216;USER_LOADED' it will change the state accordingly. You can see some further comments in the snippet above.

#### Redux store {#redux-store}

Found in:
./src/redux/stores/index.stores.js

Here we are putting together all the stuff that we created; you can read more detailed comments in the code above.

### The Redux flow

To sum up, the steps you need to follow to work with redux are:

- Set up a store, which is done generally only once
- Then, whenever you need to send to your store (which acts as a global state) some data you need to:
  - Create an action
    - If some AJAX or other side effects are required, set up a middleware to take that action
    - The middleware performs the AJAX operation, or whatever is needed
    - And it dispatches a new action, which is picked up by a reducer
  - The reducer picks up the action, and modifies the state
- In the component, the content is changed according to the data coming from Redux

## Conclusions {#conclusions}

I know there are many moving parts involved, but Redux seems like a great solution and it's probably here to stay.
What I generally like to do is to avoid almost completely the usage of component-level state, except for small UI-related information (e.g. show/hide a menu), and use Redux for everything else, with the advantage that important global state is available from anywhere in the App, I just need to "connect" to the redux store.

There is surely much more to it than what is in this guide, and I am probably just scratching the surface here, but hopefully this will be enough to get you started.

If you would like to discuss this, just do so on LinkedIn:

<blockquote class="blockquote__linkedin data-lang=" style="border-color: #1D77B5;">
  <p dir="ltr" lang="en">
    After having learnt about Redux from Valentino Gagliardi, I thought it would have been a good idea to explain it again in my own words. The more explanations, the better, so here's my contribution to the understanding of Redux for newcomers.
  </p>

  <p>
    — Alessandro Muraro &#8211; February 21, 2019
  </p>

  <p>
    <a href="https://www.linkedin.com/feed/update/urn:li:activity:6504333630175748096/">Check it out on LinkedIn</a>
  </p>
</blockquote>

&nbsp;

Photo by [Rúben Marques][12] on [Unsplash][13]

[1]: https://www.valentinog.com/blog/redux/
[2]: https://medium.com/@ohansemmanuel/table-of-contents-for-understanding-redux-1-ea0667e1453d
[3]: https://read.reduxbook.com/
[4]: https://github.com/akmur/redux-tutorial
[5]: http://localhost:3000
[6]: #react-index
[7]: #react-component
[8]: #redux-action
[9]: #redux-middleware
[10]: #redux-reducer
[11]: #redux-store
[12]: https://unsplash.com/photos/VwGcs_D_Q2w?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[13]: https://unsplash.com/search/photos/web?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
