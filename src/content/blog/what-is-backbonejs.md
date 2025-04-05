---
title: "What is BackboneJS?"
description: ""
pubDate: 2013-10-01
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

In recent years, there has been a slew of JavaScript frameworks introduced. So where’s a developer to start?

Let’s look at Backbone.JS, a nice little library that makes the process of creating complex, interactive and data driven apps much easier. It provides a clean way to separate your data from your presentation. It is a super light-weight library that lets you create easy to maintain front ends. It's backend agnostic and works well with any of the modern JavaScript libraries you're already using. You’ll notice that I said library and not framework. According to [Backbone’s official FAQ](http://backbonejs.org/ "Backbone.js"):

> Backbone is a library, not a framework, and plays well with others. You can embed Backbone widgets in Dojo apps without trouble, or use Backbone models as the data backing for D3 visualizations (to pick two entirely random examples).

[Backbone](http://backbonejs.org/ "Backbone.js") describes it’s purpose as:

> Backbone supplies structure to JavaScript-heavy applications by providing models with key-value binding and custom events, collections with a rich API of enumerable functions, views with declarative event handling, and connects it all to your existing application over a RESTful JSON interface.

What does that mean? Well let’s take it apart.

## Key-value binding and custom events

When a model's contents or state is changed, other objects that have subscribed to the model are notified so they can proceed accordingly. Here, the views listen to changes in the model, and update themselves accordingly instead of the model having to deal with the views manually.

## Rich API of enumerable functions

Backbone ships with a number of very useful functions for handling and working with your data. Unlike other implementation, arrays in JavaScript are pretty neutered, which really is a hampering problem when you have to deal with data.

## Views with declarative event handling

Your days of writing spaghetti bind calls are over. You can programmatically declare which callback needs to be associated with specific elements.

## RESTful JSON interface

Even though the default method is to use a standard AJAX call when you want to talk to the server, you can easily switch it out to anything you need. A number of adapters have sprung up covering most of the favorites including Websockets and local storage.

To put it into even simpler terms:

Backbone provides a clean way to separate your data from your presentation. The model that works with the data is only concerned with synchronizing with a server while the view's primary duty is listening to changes to the subscribed model and rendering the HTML.

With that said, let’s get into the bits and pieces. [We'll start by installing BackboneJS.](http://www.pauljeter.net/web-development/javascript/backbonejs/installing-backbonejs/ "Installing BackboneJS")

### Digging into Backbone.js series:

- What is Backbone.js?
- [Installing Backbone.js](http://www.pauljeter.net/web-development/javascript/backbonejs/installing-backbonejs/ "Installing BackboneJS")
- [Models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?")
- [Collections](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-collection/ "What is a Collection?")
- [Views](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-view/ "What is a View?")
- [Routers](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-router/ "What is a Router?")
