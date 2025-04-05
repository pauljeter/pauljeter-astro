---
title: "Building a CSS Foundation"
description: ""
pubDate: 2013-10-09
heroImage: '/images/css3.jpg'
categories: 
  - "front-porch"
tags: 
  - "css"
  - "css3"
  - "front-end"
  - "front-porch-2"
  - "frontporch-io"
  - "modular-css"
  - "sass"
  - "scss"
---

Presented by Jake Smith at the 2013 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@jakefolio](twitter.com/jakefolio)  
[http://bit.ly/VuP5d5](http://bit.ly/VuP5d5)

Specificity Kills!

CSS is easy, Naming Stuff is hard

 Clear Intent is the goal

Do not over qualify your declarations

- content
- ul#nav

Do not let your CSS dictate your HTML structure

- .content
- #nav

Let's make specificity easy

Avoid using IDs\* (only if you declare it and use it only once in your CSS)

 Modular CSS

Stop developing pages, start developing systems

- smacss
- inuitcss

Separate structure from style

Context MUST NOT modify your modules

Code Standards/Styles

- hyphen separated class names
- space between property and value
- inline only aloud with one property
- one selector per line
- 2space, 4 space vs tabs

Documentation

- backtic = \`

Predictably and consistency always wins out

CSS LINT - check your css

HTML\_CodeSniffer

In conclusion:

- Naming is hard, so be clear with your styles
- Don't let your styles define your HTML Structure
- Small modules are easier to maintain
- Consistency and Predictability always win out
- Document for tomorrow's developer
