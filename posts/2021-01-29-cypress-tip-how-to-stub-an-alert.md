---
layout: layouts/post.njk
title: "Cypress tip: how to stub an alert"
type: post
date: 2021-01-29 16:21:50
featured_image: /img/apps.jpg
url: https://alexmuraro.me/posts/2021-01-29-cypress-tip-how-to-stub-an-alert
excerpt: "I've recently started using Cypress for testing web applications, and even for unit testing. One thing that was not immediately clear to me was how to stub (aka, fake) a basic thing like an alert, so that I can listen for this alert to be called, and assert that yes, it was indeed called."
tags:
  - Testing
  - Cypress
  - Tools
---

I've recently started using Cypress for testing web applications, and even for unit testing. One thing that was not immediately clear to me was how to stub (aka, fake) a basic thing like an alert, so that I can "listen" for this alert to be called, and assert that yes, it was indeed called.
Simple enough, but took me some Googling to find how to do it, so I'm adding it here so it's more available.

## How to do it

This is my snippet of code, used in a unit test in this case:

```
it('the "handleOnClick" prop works correctly', () => {
  const stub = cy.stub()

  cy.on('window:alert', stub)

  cy.get('[data-test-id="element"]')
    .click()
    .then(() => {
      expect(stub.getCall(0)).to.be.calledWith('Hello')
    })
})
```
