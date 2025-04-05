---
title: "What is a Collection?"
pubDate: 2013-10-21
description: ""
heroImage: '/images/digging-into-backbone.jpg'
categories: 
  - "backbonejs"
tags: 
  - "backbonejs"
  - "collections"
  - "frameworks"
  - "javascript"
  - "js"
  - "libraries"
---

Collections are ordered sets of [models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?"). For example:

- Model: Book - Collection: Library
- Model: Song - Collection: Artist
- Model: Todo item - Collection: Todo List

```
var Book = Backbone.Model.extend({
    initialize: function(){
        console.log("Take a look, It's in a book, A Reading Rainbow!");
    }
});

var Library = Backbone.Collection.extend({
    model: Book
});
```

## Building a Collection

Now let's populate our collection with some useful model data.

```
Book = Backbone.Model.extend({
    defaults: {
        title: 'Not specified',
        author: 'Not specified'
    },
    initialize: function() {
        console.log("Take a look, It's in a book, A Reading Rainbow!");
    }
});

var Library = Backbone.Collection.extend({
    model: Book
});

var book1 = new Book({ title: 'To Kill a Mockingbird', author: 'Harper Lee' });
var book2 = new Book({ title: '1984', author: 'George Orwell' });
var book3 = new Book({ title: 'The Lord of the Rings', author: 'J.R.R. Tolkien' });

var myLibrary = new Library([ book1, book2, book3]);
console.log( myLibrary.models ); // [book1, book2, book3]
```

 Next, let's look at [Views](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-view/ "What is a View?").

### Digging into Backbone.js series:

- [What is Backbone.js?](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-backbonejs/ "What is BackboneJS?")
- [Installing Backbone.js](http://www.pauljeter.net/web-development/javascript/backbonejs/installing-backbonejs/ "Installing BackboneJS")
- [Models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?")
- Collections
- [Views](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-view/ "What is a View?")
- [Routers](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-router/ "What is a Router?")
