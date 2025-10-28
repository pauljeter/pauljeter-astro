---
title: "SMACSS Your Sass Up"
description: ""
pubDate: 2014-10-08
heroImage: '/images/scss.jpg'
categories: 
  - "front-porch"
tags: 
  - "conferences-2"
  - "css"
  - "css3"
  - "front-end"
  - "front-porch-2"
  - "frontporch-io"
  - "modular-css"
  - "sass"
  - "scss"
  - "web-development"
---

Presented by Mina Markham at the 2014 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@minamarkham](twitter.com/minamarkham) [@gdiDFW](twitter.com/gdiDFW) [mina.so/smacss](mina.so/smacss) [mina.so/sassyStarter](mina.so/sassyStarter)  
  
Modular CSS architecture  
CSS is easy. HARD  
  
Modular CSS

- Break down sites into modular components
- Small independent pieces that are portable

Modular, Pattern, Component, etc  
  
Scalable Modular Architecture for CSS

SMACSS is not a Framework, it is an approach

- categorization
- naming conventions
- depths aplicability

 Base

- CSS resets, default styles (h1-6, p, a)

Layout

- grid Major components (header, sidebar, footer)
- .layout- or .l-

Modules

-  content patterns (search boxes, navigation, promos)
- .<name>

States

- module in various states (active, disabled, collapsed, hidden)
- .is-\*

Themes

- module in various contexts
- .theme-\*

Naming Conventions - Categorize CSS rules  
Class Selectors - Meaningful names  
Child Selectors (only 1 deep) - shallow selectors  
  
Sass

- Nesting for naming conventions (be careful, don't go too deep)
- @extend
- @extend with %btn - placeholder selector to keep from outputting to compiled CSS

File Structure

- @import smaller files
- break modules into separate files

!important - shame.css

- put all hacks and shameful code in one place
- Sometimes hacks happen

Theming  
  
Refactor pieces at a time  
  
Squares Conference

* * *

This post is from the Front Porch Conference Series. If you enjoyed it, please check out the others below.

- [Accessibility in Not A Four-letter Word by Kim Lovering](http://www.pauljeter.net/web-development/conferences/front-porch/accessibility-in-not-a-four-letter-word-kim-lovering-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Accessibility in Not A Four-letter Word") 
- [SVG Strikes Back by Matt Baxter](http://www.pauljeter.net/web-development/conferences/front-porch/svg-strikes-back-matt-baxter-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "SVG Strikes Back")
- [How Kids Learn by Chirag Gupta](http://www.pauljeter.net/web-development/conferences/front-porch/how-kids-learn-chirag-gupta-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "How Kids Learn")
- [Intro to WebGL and Three.js by David Lyons](http://www.pauljeter.net/web-development/conferences/front-porch/intro-to-webgl-and-three-js-david-lyons-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Intro to WebGL and Three.js -David Lyons")
- [Deploying Websites with Capistrano by Andrew Turner](http://www.pauljeter.net/web-development/conferences/front-porch/deploying-websites-with-capistrano/ "Deploying Websites with Capistrano") 
- SMACSS Your Sass Up by Mina Markham
- [Developing Mobile Apps with The Ionic Framework by Justin Noel](http://www.pauljeter.net/web-development/conferences/front-porch/developing-mobile-apps-with-the-ionic-framework-justin-noel-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Developing Mobile Apps with The Ionic Framework -Justin Noel")
- [Context Aware CSS by Matthew Carver](http://www.pauljeter.net/web-development/conferences/front-porch/context-aware-css-matthew-carver-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Context Aware CSS")
