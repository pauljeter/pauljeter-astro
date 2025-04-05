---
title: "What is a View?"
description: ""
pubDate: 2013-10-31
categories: 
  - "backbonejs"
tags: 
  - "backbonejs"
  - "frameworks"
  - "javascript"
  - "js"
  - "libraries"
  - "views"
heroImage: '/images/digging-into-backbone.jpg'
---

According to the BackboneJS documentation:

> Backbone views are almost more convention than they are code , they don't determine anything about your HTML or CSS for you, and can be used with any JavaScript templating library.

Views are used to organize your UI into logical views. Your views are connected to [models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?"), and both can be updated independently when the model is changed, without the need to re-render the entire page. Instead of parsing a JSON object, looking up an element in the DOM, and updating the HTML by hand, you can instead bind your view's "render" function to the model's "change" event. Then, anywhere that model data is displayed in your app's UI, it will always be up to date.

```
ListView = Backbone.View.extend({
    initialize: function(){
        alert("Reading is Fun!");
    }
});

// The initialize function is always called when instantiating a Backbone View.
// Consider it the constructor of the class.
var list_view = new ListView();
```

## The "el" property

The "el" property references the DOM object created in the browser. Every [Backbone.js](http://backbonejs.org "BackboneJS") view has an "el" property, and if it not defined, Backbone.js will construct its own, which is an empty div element.

Let's set our view's "el" property to div#list\_container, effectively making Backbone.View the owner of the DOM element.

FYI: This binds the container element, so any events you trigger must be in this element.

```
<div id="list_container"></div>

<script type="text/javascript">
    ListView = Backbone.View.extend({
        initialize: function(){
            alert("Reading is Fun!");
        }
    });

    // The initialize function is always called when instantiating a Backbone View.
    // Consider it the constructor of the class.
    var list_view = new ListView({ el: $("#list_container") });
</script>
```

## Loading a template

Backbone.js is dependent on [Underscore.js](http://documentcloud.github.com/underscore/ "Underscore.js"), which includes its own micro-templating solution. I prefer to use [Handlebars.js](http://handlebarsjs.com/ "Handlebars.js") for templating with Backbone.js. We will look more at Handlebars.js in a future article. For this example, we will use the for simple, built in Underscore.js solution.

Let's implement a "render()" function and call it when the view is initialized. The "render()" function will load our template into the view's "el" property using jQuery.

```
<script type="text/template" id="list_template">
  <h2>Books List</h2>
  <h3>Title: <%= title %></h3>
  <h4>Author: <%= author %></h4>
</script>

<div id="list_container"></div>

<script type="text/javascript">
    var Book = Backbone.Model.extend({
        defaults: {
            title: 'Not specified',
            author: 'Not specified'
        },
        initialize: function() {
            console.log("Take a look, It's in a book, A Reading Rainbow!");
        }
    });

    var book1 = new Book({
        title: 'To Kill a Mockingbird',
        author: 'Harper Lee'
    });

    ListView = Backbone.View.extend({
        initialize: function() {
            console.log("Reading is Fun!");
            //this.render();
        },
        template: _.template($("#list_template").html()),
        render: function() {
            this.$el.html(this.template(this.model.attributes));
            return this;
        }
    });

    var list_view = new ListView({
        el: $("#list_container"),
        model: book1
    });
</script>
```

## Listening for events

To attach a listener to your view, you use the "events" attribute of Backbone.View. Remember that event listeners can only be attached to child elements of the "el" property. Let's attach a "click" listener to a button.

```
<script type="text/template" id="list_template">
  <h2>Books List</h2>
  <h3>Title: <%= title %></h3>
  <h4>Author: <%= author %></h4>
  <button>Re-render</button>
</script>

<div id="list_container">
    <button>Click the button to render</button>
</div>

<script type="text/javascript">
    var Book = Backbone.Model.extend({
        defaults: {
            title: 'Not specified',
            author: 'Not specified'
        },
        initialize: function() {
            console.log("Take a look, It's in a book, A Reading Rainbow!");
        }
    });

    var book1 = new Book({
        title: 'To Kill a Mockingbird',
        author: 'Harper Lee'
    });

    ListView = Backbone.View.extend({
        events: {
            "click button": "render"
        },
        initialize: function() {
            console.log("Reading is Fun!");
            //this.render();
        },
        template: _.template($("#list_template").html()),
        render: function() {
            this.$el.html(this.template(this.model.attributes));
            return this;
        }
    });

    var list_view = new ListView({
        el: $("#list_container"),
        model: book1
    });
</script>
```

This article just scratches the surface of what can be done with Backbone.js views. You can listen for events on the model, delegate events and much, much more. For a working example of this view, follow this link to [jsFiddle](http://jsfiddle.net/pauljeter/58zmx4zf/2/ "Backbone.js View on jsFiddle"). Next, we will look at [Routers](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-router/ "What is a Router?").

### Digging into Backbone.js series:

- [What is Backbone.js?](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-backbonejs/ "What is BackboneJS?")
- [Installing Backbone.js](http://www.pauljeter.net/web-development/javascript/backbonejs/installing-backbonejs/ "Installing BackboneJS")
- [Models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?")
- [Collections](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-collection/ "What is a Collection?")
- Views
- [Routers](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-router/ "What is a Router?")
