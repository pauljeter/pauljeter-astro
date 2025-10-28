---
title: "What is a Model?"
pubDate: 2013-10-14
description: ""
heroImage: '/images/digging-into-backbone.jpg'
categories: 
  - "backbonejs"
tags: 
  - "backbonejs"
  - "frameworks"
  - "javascript"
  - "js"
  - "libraries"
  - "models"
---

Depending on which MVC you ask, you will get various answers to this question. The creators of [BackboneJS](http://backbonejs.org "BackboneJS") make it clear what a model is in a BackboneJS application. From their documentation:

> Models are the heart of any JavaScript application, containing the interactive data as well as a large part of the logic surrounding it: conversions, validations, computed properties, and access control.

 So for the purpose of the tutorial let's create a model.

```
Book = Backbone.Model.extend({
        initialize: function() {
            alert('Hello World');
    }
});

var book = new Book;
```

initialize() is triggered when a new instance of a model( models, collections and views work the same way ) are created. It's not required to be included in your model declaration but you will find it useful more often than not.

##  Setting attributes

 Next, you will want to pass parameters when you create an instance of your model.

```
Book = Backbone.Model.extend({
    initialize: function() {
        alert('Hello World');
    }
});

var book = new Book({
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee'
});
// You can also set it afterwards
// These operations are equivelent
var book = new Book();
book.set({
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee'
});
```

Therefor, passing a JavaScript object into our constructor is the same as calling model.set(). Now you can retrieve the attributes from these models.

## Getting attributes

You can access the model properties anytime after they have been set, using the model.get() method.

```
Book = Backbone.Model.extend({
    initialize: function() {
        alert('Hello World');
    }
});

var book = new Book({
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee'
});

var title = book.get('title'); // To Kill a Mockingbird
var author = book.get('author'); // Harper Lee
```

## Setting model defaults

 Sometimes you will want your model to contain default values. This can easily be accomplished by setting a property name 'defaults' in your model declaration.

```
Book = Backbone.Model.extend({
    defaults: {
        title: 'The Lord of the Rings',
        author: 'J.R.R. Tolkien '
    },
    initialize: function() {
        alert('Hello World');
    }
});

var book = new Book({
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee'
});

var title = book.get('title'); // To Kill a Mockingbird
var author = book.get('author'); // Harper Lee
```

## Listening for changes to the model

Let's talk about one of the more useful functionalities of a Backbone Model. All of the attributes of a model can have listeners bound to them. These listeners can detect changes to their values. In your initialize function, you can bind a function to be called every time the value of your attribute is changed. In this case, if the tile of our "book" changes, we will alert the new title.

```
Book = Backbone.Model.extend({
    initialize: function() {
        alert('Hello World');
        this.on('change:title', function(model) {
            var title = model.get('title'); // '1984'
            alert('Changed my title to ' + title);
        });
    }
});

var book = new Book({
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee'
});

book.set({
    title: '1984'
});
// This triggers a change and will alert()
```

You can bind the change listener to the individual attributes, or you can bind it to listen to all of the attributes in the model. Do this by using "this.on(‘change', function(model){});" without the :attribute.

This was a very basic overview of Backbone models. We will get more in-depth as the series goes on. Next, let's look at [Collections](http://www.pauljeter.net/random-thoughts/what-is-a-backbonejs-collection/ "What is a Collection?").

### Digging into Backbone.js series:

- [What is Backbone.js?](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-backbonejs/ "What is BackboneJS?")
- [Installing Backbone.js](http://www.pauljeter.net/web-development/javascript/backbonejs/installing-backbonejs/ "Installing BackboneJS")
- Models
- [Collections](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-collection/ "What is a Collection?")
- [Views](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-view/ "What is a View?")
- [Routers](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-router/ "What is a Router?")
