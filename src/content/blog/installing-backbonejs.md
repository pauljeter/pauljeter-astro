---
title: "Installing BackboneJS"
description: ""
pubDate: 2013-10-07
heroImage: '/images/digging-into-backbone.jpg'
categories: 
  - "backbonejs"
tags: 
  - "backbonejs"
  - "frameworks"
  - "javascript"
  - "js"
  - "libraries"
---

Getting started and installing is easy. First, go to the [Backbone.js](http://www.backbonejs.org "BackboneJS") website and download the development or production file of the latest stable version. Then download the dependancies.

##  Dependancies

 BackboneJS’s only dependancies are [jQuery](http://jquery.com/download/ "jQuery Downloads") and [UnderscoreJS](http://underscorejs.org/ "UnderscoreJS"). Underscore provides many helper methods and can be interchanged with [Lo-Dash](http://lodash.com/ "Lo-Dash") (more about this in future articles).

##  Installation

 To set up your environment, all that you need to do is include those three files.

```
<!DOCTYPE html>
  <html lang="en">
      <head>
          <meta charset="utf-8">
      </head>
          <body>
              <script src="js/underscore.js"></script>
              <script src="js/jquery.js"> </script>
              <script src="js/backbone.js"></script>
          </body>
  </html>
```

That’s it! Now you can start developing your Single Page Apps. [Next, we’ll dive into Backbone Models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a BackboneJS Model?").

### Digging into Backbone.js series:

- [What is Backbone.js?](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-backbonejs/ "What is BackboneJS?")
- Installing Backbone.js
- [Models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?")
- [Collections](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-collection/ "What is a Collection?")
- [Views](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-view/ "What is a View?")
- [Routers](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-router/ "What is a Router?")
