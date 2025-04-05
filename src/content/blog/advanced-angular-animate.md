---
title: "Advanced angular-animate"
description: ""
pubDate: 2015-03-04
categories: 
  - "ng-conf"
tags: 
  - "angularjs"
  - "conferences-2"
  - "css"
  - "css3"
  - "frameworks"
  - "front-end"
  - "greensock-js"
  - "javascript"
  - "js"
  - "modular-css"
  - "ng-conf"
  - "selectors"
  - "web-development"
heroImage: "/images/ng-conf-2015.jpg"
---

Presented by Lukas Ruebbelke at the 2015 ng-conf in Salt Lake City, Utah.

@simpulton

angular-animate is just the candy shell on your chocolaty CSS/JS animations.

ng-fx

Events & Convention

Events

- enter
- leave
- move
- addClass
- removeClass

Convention

\[class\]\[event\]\[state\]

```
.repeat-item.ng-leave.ng-leave-active
```

```
/* you can also define the trasition style on the base class as well (.repeat-item) */

.repeat-item.ng-enter,
.repeat-item.ng-leave {
  transition: 0.5s linear all;
}

.repeat-item.ng-enter,
.repeat-item.ng-leave.ng-leave-active {
  opacity: 0;
}

.repeat-item.ng-enter.ng-enter-active,
.repeat-item.ng-leave {
  opacity: 1;
}
```

JavaScript:

```
myApp.animation('.fade', function() {
  reture {
    // call done when the animation is over
    enter: function(element, done) {}

    // leave and move are the same as enter
      leave: function(element, done) {}
    move: function(element, done) {}

    // this is called BEFORE the class is added
      beforeAddClass: function(element, className, done) {}

    // this is called AFTER the class is added
      addClass: function(element, className, done) {}

    // this is called BEFORE the class is removed
      beforeRemoveClass: function(element, className, done) {}

    // this is called AFTER the class is removed
      removeClass: function(element, className, done) {}

  };
})
};
```

Greensock.js animation library

Live Coding.

* * *

This post is from the ng-conf Series. If you enjoyed it, please check out the others below.

-  [Functional Testing with Protractor](http://www.pauljeter.net/web-development/conferences/ng-conf/protractor-testing-in-angularjs-ben-clikinbeard-2015-ngconf/ "Functional Testing with Protractor")
- [Angular Forms with angular-formly](http://www.pauljeter.net/web-development/conferences/ng-conf/angular-forms-with-angular-formly-kent-c-dodds-2015-ng-conf/ "Angular Forms with angular-formly")
- Advanced angular-animate
