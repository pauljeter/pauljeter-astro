---
title: "Should I Use ng-if or ng-show/ng-hide?"
description: ""
pubDate: 2014-10-23
heroImage: '/images/angularjs-2.jpg'
categories: 
  - "angularjs"
tags: 
  - "angularjs"
  - "directive"
  - "framework"
  - "javascript"
  - "libraries"
  - "ng-hide"
  - "ng-if"
  - "ng-show"
---

In my experience, most developers that are new to AngularJS tend to over use the ng-show and ng-hide directives. The truth of the matter is that the ng-if directive is very similar, with one subtle but important difference.

## `ng-if`

`ng-if` will remove elements from DOM. This means that all your handlers or anything else attached to those elements will be lost. For example, if you bound a click handler to one of child elements, when `ng-if` evaluates to false, that element will be removed from DOM and your click handler will not work any more, even after `ng-if` later evaluates to true and displays the element. You will need to reattach the handler.

## `ng-show/ng-hide`

`ng-show/ng-hide` does not remove the elements from DOM. It uses CSS styles to hide/show elements (note: you might need to add your own classes). This way your handlers that were attached to children will not be lost.

Elements that are not in the DOM have less performance impact and your web app might appear to be faster when using `ng-if` compared to `ng-show/ng-hide`. In my experience, the difference is negligible. Animations are possible when using both ng-show/ng-hide and ng-if, with examples for both in the Angular documentation.

Ultimately, the question you need to answer is whether you can remove element from DOM or not?
