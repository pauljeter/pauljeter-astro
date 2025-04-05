---
title: "Using Modernizr to Progressively Enhance your CSS"
description: ""
pubDate: 2013-10-09
heroImage: '/images/modernizr.jpg'
categories: 
  - "front-porch"
tags: 
  - "conferences-2"
  - "front-end"
  - "frontporch-io"
  - "javascript"
  - "jquery"
  - "modernizr"
  - "web-development"
---

Presented by Matthew Carver at the 2013 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@matthew\_carver](twitter.com/matthew_carver)  
[manning.com/carver](manning.com/carver)  
[bigspaceship.com](bigspaceship.com)

- There's more to being device agnostic that the width of the device
- The clock is ticking on IE8
- The clock is ticking on desktop computers
- Tablets are just easier to use, (because they do less)
- The third world is coming online (older systems will stay in the ecosystem longer)
- All of this means one thing: Diversity

Progressive Enhancement - To improve a site starting from the smallest subset of supported features

1. Base - identify a staring point
2. Build - build to those specifications
3. Test - test your work
4. Enhance - start adding flare

Base

- Starting point
- examles:
    - JS disabled handheld device
    - desktop computer running IE7
- The business defines your starting point

Build

- get to making - this is very much a prototyping phase

Test

- Real world testing
- test in the real places where your users will use

Improve

- Enhancements
- add environments

In order to do this, we needed a tool that could appropriate what CSS and JS should be served to each browser  
  
Modernizr

- 40 tests available out of the box

ADDTEST()

- allows you to add tests to modernizr

MODERNIZR.LOAD()

- allows you to load files only when they are required
- load files based on modernizr tests

MODERNIZR.MQ()

- media query testing
