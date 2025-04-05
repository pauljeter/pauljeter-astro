---
title: 'Control Scope in Sass Components with BEM'
description: 'Learn how to manage CSS scope effectively by using the `$self` variable in Sass, inspired by JavaScript scoping techniques, to write cleaner and more maintainable BEM components.'
pubDate: '2017-07-10'
heroImage: '/images/bem-sass.jpg'
category: 'CSS'
tags: ['Sass', 'BEM', 'CSS']
---

When working with CSS and Sass, controlling scope isn't always top of mind. While we typically rely on the ampersand (`&`) for nesting selectors, this approach can quickly become confusing and lead to bloated, hard-to-manage CSS.

Interestingly, JavaScript developers have long solved a similar scope issue by assigning the value of `this` to a variable called `self`. Could we use this technique to manage scope more effectively in Sass? Absolutely!

## A JavaScript Primer: Understanding Scope with `self`

In JavaScript, we often assign `this` to a variable like `self` to maintain a predictable context, especially in closures, event listeners, or asynchronous functions.

Here's an example:

```javascript
function foo() {
  let self = this;

  return function() {
    // self is always `foo`, even inside this closure
    return self;
  }
}

let bar = new foo();
```

Let's make this clearer with an event listener example. Given this HTML markup:

```html
<div class="component">
  <div class="component__child-element"></div>
</div>
<div class="component">
  <div class="component__child-element"></div>
</div>
```

Using JavaScript without `self`, we have this issue:

```javascript
function foo() {
  let childElements = [...document.querySelectorAll('.component__child-element')];

  childElements.forEach(element => {
    element.addEventListener('click', function(evt) {
      // `this` refers to the clicked element
      console.log(this);
    });
  });
}

let bar = new foo();
```

Clicking an element logs the clicked element itself, not the instance of `foo`.

Using `self` to store context:

```javascript
function foo() {
  let self = this;

  let childElements = [...document.querySelectorAll('.component__child-element')];

  childElements.forEach(element => {
    element.addEventListener('click', function(evt) {
      // `self` correctly refers to the instance of foo
      console.log(self);
    });
  });
}

let bar = new foo();
```

Now, clicking the element logs the correct context (`foo`), showcasing effective scope management.

## How Does This Relate to Sass?

Let's transfer this concept to Sass and manage CSS scope similarly with a `$self` variable.

Given this markup:

```html
<div class="component">
  <div class="component__child-element"></div>
</div>
<div class="component component--reversed">
  <div class="component__child-element"></div>
</div>
```

We have some basic Sass:

```scss
.component {
  display: block;
  max-width: 30rem;
  min-height: 30rem;
  margin: 5rem auto;
  background: rebeccapurple;
  position: relative;
  border: 1px dashed rebeccapurple;

  &__child-element {
    width: 15rem;
    height: 15rem;
    border-radius: 50%;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate3d(-50%, -50%, 0);
    background: white;
  }
}
```

We now want to add a reversed modifier that swaps colors. Intuitively, you might try:

```scss
.component {
  &--reversed {
    background: white;
    border-color: lightgray;

    &__child-element {
      background: rebeccapurple;
    }
  }
}
```

But this doesn't work! The nested `&__child-element` compiles incorrectly to `.component--reversed__child-element`.

## Using `$self` to Control Scope

Let's solve this by setting our root context to a variable, `$self`:

```scss
.component {
  $self: &; // This is now `.component`

  display: block;
  max-width: 30rem;
  min-height: 30rem;
  // other styles...

  &--reversed {
    background: white;
    border-color: lightgray;

    // Using $self to correctly scope the child element
    #{$self}__child-element {
      background: rebeccapurple;
    }
  }
}
```

This now compiles correctly to:

```css
.component--reversed .component__child-element {
  background: rebeccapurple;
}
```

## Taking `$self` Further: Cleaner BEM Structure

One practice I enjoy is referencing modifiers directly within the element declaration, grouping styles neatly. For example:

```scss
.component {
  $self: &;

  &__child-element {
    width: 15rem;
    height: 15rem;
    background: white;

    // Modify element when parent is reversed
    #{$self}--reversed & {
      background: rebeccapurple;
    }
  }
}
```

The selector compiles exactly how we want it:

```css
.component--reversed .component__child-element {
  background: rebeccapurple;
}
```

## An Advanced Example: Sibling Selectors

Let's say we have multiple grids. We want each subsequent grid's items styled differently:

```scss
.grid {
  $self: &;

  &__item {
    // Default styles...

    // Change item color for sibling grids
    #{$self} + #{$self} & {
      background: rebeccapurple;
    }
  }
}
```

The compiled CSS is powerful and clean:

```css
.grid + .grid .grid__item {
  background: rebeccapurple;
}
```

Using `$self` this way ensures flexibility and clarity even in complex scenarios.

## Wrapping Up

By borrowing a page from JavaScript's playbook, we've effectively managed scope in Sass. Setting `$self: &` at the root of your component gives you more control over your selectors, resulting in cleaner, more maintainable CSS. Give it a try, it could revolutionize how you structure your BEM components.
