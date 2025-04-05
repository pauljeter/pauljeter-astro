---
title: 'Common Backbone.js Patterns and Tips'
description: 'Explore essential design patterns, solutions, and common mistakes in Backbone.js applications, including deep object copying, model facades, and performance tips.'
pubDate: '2013-12-19'
heroImage: '/images/digging-into-backbone.jpg'
category: 'JavaScript'
tags: ['Backbone.js', 'Design Patterns', 'JavaScript']
---

Backbone.js is a powerful, lightweight JavaScript framework that provides structure for client-side applications. However, because it offers minimal structure, developers often encounter common issues or pitfalls, especially when first adopting Backbone.js. In this guide, I'll cover some essential design patterns and common pitfalls that can improve your Backbone.js applications.

## Deep Copying Objects

JavaScript treats primitive variables as pass-by-value and objects as pass-by-reference. Backbone.js returns references to objects stored in models. If you directly modify these references, you'll unintentionally change the model data. Consider this example:

```javascript
const Person = Backbone.Model.extend({
  defaults: {
    name: 'John Doe',
    address: {
      street: 'Main Street',
      city: 'Dallas',
      state: 'TX',
      zipCode: 75202
    }
  }
});

const person = new Person({ name: 'Paul J' });

const address = person.get('address');
address.zipCode = 'Hello World';

// Modifying 'address' affects the model unintentionally!
```

### Solution:
Perform a deep copy to avoid this issue. Using jQuery's `$.extend()` is effective:

```javascript
const address = $.extend(true, {}, person.get('address'));
```

## Creating Facades for Model Data

JSON responses from APIs frequently change. To shield your views from such changes, create getter methods within your models to abstract underlying data structures:

```javascript
const Hotel = Backbone.Model.extend({
  defaults: {
    rooms: []
  },

  getRoomsByBed: function(bed) {
    return _.filter(this.get('rooms'), { bed: bed });
  }
});
```

If your API changes the rooms data structure from an array to an object, you only need to adjust the getter method without breaking your view logic.

## Storing Non-Server Data in Models

Sometimes, models or collections need to store client-side information that isn't persisted to the server. This practice simplifies view interactions and avoids costly DOM operations:

```javascript
const View = Backbone.View.extend({
  events: {
    'click #items li a': 'selectItem'
  },

  selectItem: function(e) {
    const selectedId = $(e.currentTarget).data('id');
    this.model.set('selectedItemId', selectedId);
  }
});
```

However, carefully evaluate this pattern, as it can blur lines between data and presentation logic.

## Partially Rendering Views

Fully re-rendering views on every model change can degrade performance. Instead, render only the parts of the view tied to the changed attributes:

```javascript
const View = Backbone.View.extend({
  initialize: function() {
    this.listenTo(this.model, 'change:a', this.renderA);
    this.listenTo(this.model, 'change:b', this.renderB);
  },

  renderA: function() {
    $('#a', this.$el).text(this.model.get('a'));
  },

  renderB: function() {
    $('#b', this.$el).text(this.model.get('b'));
  }
});
```

## Keeping Models View-Agnostic

Models and collections should be independent of view logic. This separation ensures better modularity, easier maintenance, and reduced complexity.

- **Good**: Models handle data, views handle rendering.
- **Bad**: Models directly manipulate or reference views.

## Parameter Mapping in Routers

Backbone.js does not automatically map URL parameters semantically. To avoid bloated router methods, explicitly handle route parameters within your routing functions:

```javascript
const Router = Backbone.Router.extend({
  routes: {
    'search/:foo': 'search',
    'search/:foo/:bar': 'search'
  },

  search: function(foo, bar) {
    const params = { foo: foo || null, bar: bar || null };
    // handle parameters
  }
});
```

## Understanding `model.fetch()`

The `fetch()` method does not replace the entire model; instead, it merges new data into existing attributes. Remember to explicitly reset your model attributes if needed.

## Using Proper IDs with PUT Requests

Backbone requires models to have an ID attribute to perform PUT requests. Use `idAttribute` to specify alternative IDs from your server responses:

```javascript
const Car = Backbone.Model.extend({
  idAttribute: 'carID'
});
```

## Initializing Models on Page Load

To optimize initial rendering, embed initial JSON data directly into your HTML, allowing models and collections to initialize immediately:

```javascript
<script>
  var model = new Model(<%= @model.to_json.html_safe %>);
</script>
```

## Handling Validation Errors in Models

Handling validation errors requires careful design. Two common approaches are:

- **Return error objects**:
```javascript
validate: function(attrs) {
  const errors = [];
  if (!attrs.name) {
    errors.push({ field: 'name', message: 'Name is required.' });
  }
  return errors.length ? errors : null;
}
```

- **Broadcast custom error events**:
```javascript
validate: function(attrs) {
  if (!attrs.email) {
    this.trigger('invalid:email', 'Email is required.');
  }
}
```

Both have their merits; choose based on your application's complexity.

## Generic Error Display Views

Create a generic error-handling view to consistently display validation or server-side errors throughout your application:

```javascript
const AlertView = Backbone.View.extend({
  show: function(type, message) {
    $('.alert').removeClass().addClass('alert ' + type).text(message).fadeIn().delay(5000).fadeOut();
  }
});
```

## Updating Titles in Single-Page Applications

When developing single-page applications (SPA), update document titles to reflect the current view or page state. A simple Backbone plugin or router extension can automate this:

```javascript
const Router = Backbone.Router.extend({
  initialize: function() {
    this.on('route', function(route) {
      document.title = this.titles[route] || 'Default Title';
    });
  }
});
```

## Caching Backbone Objects

Cache frequently used models and views to optimize performance, but manage this carefully to avoid memory leaks:

```javascript
initialize: function() {
  this.cached = {
    view: null,
    model: null
  };
},

index: function() {
  if (!this.cached.model) this.cached.model = new Model();
  if (!this.cached.view) this.cached.view = new View({ model: this.cached.model });
}
```

---

By leveraging these patterns and understanding common pitfalls, you'll create robust, maintainable Backbone.js applications.
