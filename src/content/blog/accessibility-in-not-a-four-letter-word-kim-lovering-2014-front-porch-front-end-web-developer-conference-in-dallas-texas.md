---
title: "Accessibility in Not A Four-letter Word"
description: ""
pubDate: 2014-10-08
heroImage: '/images/front-porch-2014.jpg'
categories: 
  - "front-porch"
tags: 
  - "accessibility"
  - "front-end"
  - "front-porch-2"
  - "frontporch-io"
  - "web-development"
---

Presented by Kim Lovering at the 2014 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@klovering](twitter.com/klovering)  
  
What is web accessibility?

- Clean organized code
- Hidden extras for those needing non-visual cues
- fairly easy to implement in a new code base excruciatingly painful when retrofitting

Why?

- Moral Obligation. Don’t be a jerk
- Don’t cut off users
- Americans with disabilities act (its the law)

It’s not just for the blind, People.

- Visual Disabilities
    - Low vision, legally blind color blindness
- Hearing Impairments
    - Hard of hearing, deafness
- Physical Disablities
    - inability to use mouse
- Cognitive Disabilities

Great, so now what?  
These don’t guarantee an accessible site, but they represent a great starting point.

- Document Structure
- Image alt text
- table structure
- Link Text

Document Structure

- Content order
- Header order
- Skip links
- Keyboard Accessible

Image Alt Text  
This seems basic, but it’s amazing the quality of code that you can find out there.

- Contextual meaning? Use <img alt=“description here”>
- Purely decorative? Throw it in your CSS as a background image or use bland alt.
- Caption cover your info? Use a blank alt. (only if the image isn’t wrapped with an individual link).

Table Structure

- Table summary an caption are great additions
- Defining your table headers (th) are the most important

Link Text  
Links that are just “click here”, “select”, “learn more” are too ambiguous for a user not being presented any other information.

- Use hidden text to allow links to be unique and clear

Some Others

- ARIA
- Color Contrast
- JavaScript Accessibility
- Landmarks
- Focus
- Zooming
- Many, many more

Testing Tools

- Wave Toolbar -FF
- Accessibility Evaluation Toolbar -FF
- Chrome Developer Tools (audit) -Chrome
- Color contrast Checker
- CynthiaSays.com
- There is a big list on W3C

Screen Readers

- JAWS -Windows
- WindowEyes -Windows
- NVDA -Windows
- Orca -Linux
- ChromeVox -web
- VoiceOver -osx
- Talkback -Android

Maintaining

- Unit test
- Manual Testing
- Developer guidelines
- QA Guidelines
- Continuous monitoring and coverage

Resources

- WebAIM.org
- W3C Accessibility Guidelines (WCAG) 2.0
- Section508.gov
- Dequeuniversity.com
- SBBartGroup.com

* * *

This post is from the Front Porch Conference Series. If you enjoyed it, please check out the others below.

- Accessibility in Not A Four-letter Word by Kim Lovering
- [SVG Strikes Back by Matt Baxter](http://www.pauljeter.net/web-development/conferences/front-porch/svg-strikes-back-matt-baxter-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "SVG Strikes Back")
- [How Kids Learn by Chirag Gupta](http://www.pauljeter.net/web-development/conferences/front-porch/how-kids-learn-chirag-gupta-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "How Kids Learn")
- [Intro to WebGL and Three.js by David Lyons](http://www.pauljeter.net/web-development/conferences/front-porch/intro-to-webgl-and-three-js-david-lyons-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Intro to WebGL and Three.js -David Lyons")
- [Deploying Websites with Capistrano by Andrew Turner](http://www.pauljeter.net/web-development/conferences/front-porch/deploying-websites-with-capistrano/ "Deploying Websites with Capistrano") 
- [SMACSS Your Sass Up by Mina Markham](http://www.pauljeter.net/web-development/conferences/front-porch/smacss-your-sass-up-mina-markham-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "SMACSS Your Sass Up")
- [Developing Mobile Apps with The Ionic Framework by Justin Noel](http://www.pauljeter.net/web-development/conferences/front-porch/developing-mobile-apps-with-the-ionic-framework-justin-noel-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Developing Mobile Apps with The Ionic Framework -Justin Noel")
- [Context Aware CSS by Matthew Carver](http://www.pauljeter.net/web-development/conferences/front-porch/context-aware-css-matthew-carver-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Context Aware CSS")
