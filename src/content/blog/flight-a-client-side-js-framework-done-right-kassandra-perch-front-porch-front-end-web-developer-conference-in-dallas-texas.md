---
title: "Flight: A client-side JS framework done right, Kassandra Perch"
description: ""
pubDate: 2013-10-09
heroImage: '/images/flightjs.jpg'
categories: 
  - "front-porch"
tags: 
  - "flightjs"
  - "framework"
  - "frameworks"
  - "front-end"
  - "front-porch-2"
  - "javascript"
  - "js"
  - "web-development"
---

Presented by Kassandra Perch at the 2013 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@kassandra\_perch](twitter.com/kassandra_perch)  
[http://github.com/flightjs](http://github.com/flightjs)

- it's small
- it's not prescriptive
- it leverages HTML and the DOM
- 5k gzipped
- requires jQuery
- uses Require.js
- Prescribes best practices for you JS code

Leverages HTML/DOM

- Components are based on small bits of HTML that handle user interaction
- Uses DOM events, which are handled well in the browser
- Components are not returned on attach
- they can only respond to events
- this enforces a truly modular code structure

Mixins

- We don't need a class system for components
- using the functional mixin system, we share code without hassle
- creates scalable, re-usable code
- Mixin is overridden by specifics of component (like SASS/LESS mixins)
- You can use multiple mixins
- Easy integration
- natural scalability
- testable front-end JS

Steps to integrate with existing codebase

- set up event handlers in your existing codebase. (that's it!)

Natural Scalablitiy

- if you use components as flight intends, and break shared code into mixins, you've worked yourself into a scalable

Testable front-end JS

- Flight components are made to react the same way to the same events. No matter the context

Bower is required\*

Check out the testing libraries

- mocha-flight
- jasmine-flight

Check ou the internal APIs

- most can be used outside of flight

Write about what you
