---
title: 'BEM: A Methodology for Maintainable CSS'
description: 'Learn how the Block, Element, Modifier (BEM) methodology helps developers create scalable and maintainable CSS through clear, structured naming conventions.'
pubDate: '2017-06-10'
heroImage: '/images/bem.jpg'
category: 'CSS'
tags: ['CSS', 'BEM', 'Frontend Development']
---

The **Block, Element, Modifier (BEM)** methodology is a popular approach for naming CSS classes, originally developed by the team at Yandex. Its primary goal is to clearly define the relationship between HTML markup and CSS styles, making codebases easier to understand and maintain.

## What is BEM?

BEM stands for:

- **Block**: A standalone entity or component (e.g., a button).
- **Element**: A part of a block that cannot be used separately (e.g., button text).
- **Modifier**: A variation of a block or element, altering its appearance or behavior.

Here's how a developer might structure CSS using BEM:

```css
/* Block component */
.btn {}

/* Element inside the block */
.btn__price {}

/* Modifier altering the block */
.btn--orange {}
.btn--large {}
```

The corresponding HTML might look like this:

```html
<a class="btn btn--large btn--orange" href="https://example.com">
  <span class="btn__price">$9.99</span>
  <span class="btn__text">Subscribe</span>
</a>
```

This structured naming makes the relationship between classes immediately clear, even to developers unfamiliar with the project's CSS.

## Advantages of BEM

Here are several reasons why adopting BEM can significantly benefit your projects:

### 1. Clear Structure and Predictability
With BEM, it's straightforward to understand how components relate. You can quickly determine existing elements and modifiers, making it easier to reuse styles without creating unnecessary classes.

### 2. Improved Readability and Maintainability
When developers see `.btn__price`, they instantly recognize it as a child element dependent on `.btn`. This clarity reduces confusion and the potential for mistakes.

### 3. Easier Team Communication
BEM provides a shared vocabulary that developers, designers, and other team members can use to discuss design components effectively, ensuring everyone stays aligned.

### 4. Enhanced Developer Confidence
As Harry Roberts highlights, adopting a methodology like BEM increases developer confidence. Developers understand exactly what a piece of code affects, making them less fearful about modifying or removing styles.

Philip Walton echoes this sentiment, emphasizing that strict adherence to BEM gives you confidence that CSS changes won’t create unexpected side-effects.

### 5. Low CSS Specificity
By relying primarily on flat, single-class selectors, BEM helps maintain low specificity, reducing the likelihood of CSS conflicts.

## Common Pitfalls with BEM

While BEM offers significant advantages, there are a few things to keep in mind to avoid misusing it:

### Avoid Nested Selectors
Avoid using nested selectors like this:

```css
.nav .nav__listItem .btn--orange {
  background-color: green;
}
```

This breaks BEM conventions by increasing specificity unnecessarily and creating confusion about the component structure.

### Don't Override Styles Between Blocks
A block or modifier should never affect another unrelated block. Doing so obscures the relationship between classes and damages the readability and maintainability of your code.

### Avoid Misusing Elements Without Their Parent Block
Incorrectly placing an element from one block inside another can cause confusion:

```html
<a class="btn">
  <div class="nav__listItem">Item one</div>
</a>
```

Here, `.nav__listItem` is incorrectly nested in `.btn`, breaking clear component boundaries.

## BEM in Action

Here are practical examples illustrating BEM clearly:

### Accordion Example

```html
<div class="accordion">
  <div class="accordion__header">Header</div>
  <div class="accordion__copy accordion__copy--open">Content</div>
</div>
```

- **Block**: `.accordion`
- **Elements**: `.accordion__header`, `.accordion__copy`
- **Modifier**: `.accordion__copy--open`

### Navigation Example

```html
<nav class="nav">
  <ul class="nav__list">
    <li class="nav__item nav__item--active"><a href="#" class="nav__link">Home</a></li>
    <li class="nav__item"><a href="#" class="nav__link">About</a></li>
  </ul>
</nav>
```

- **Block**: `.nav`
- **Elements**: `.nav__list`, `.nav__item`, `.nav__link`
- **Modifier**: `.nav__item--active`

## Criticisms of BEM

Some developers find the BEM syntax visually heavy due to double underscores and dashes. However, these symbols clearly indicate relationships and modifiers, which is precisely their strength. If you prefer another unique delimiter, you can choose one, but consistency is key.

Another criticism is that BEM may feel verbose for simple projects. However, as complexity grows, the benefits in clarity and maintainability become increasingly valuable.

Alternative methodologies like SMACSS or OOCSS handle similar concerns with different naming conventions. They can offer simpler alternatives, but each has trade-offs regarding clarity and specificity control.

## BEM with Sass

If you're using Sass and enjoy nested syntax, you can still maintain flat CSS specificity with the `@at-root` directive:

```scss
.block {
  @at-root #{&}__element {}
  @at-root #{&}--modifier {}
}
```

This compiles to:

```css
.block {}
.block__element {}
.block--modifier {}
```

## Final Thoughts

While BEM isn’t a universal solution to every CSS problem, it is a powerful methodology for creating scalable, maintainable, and collaborative front-end code. It establishes clear boundaries, consistent naming conventions, and reduces the risk of unwanted side-effects, all of which help your projects remain robust and adaptable over time.

Adopting BEM or a similar structured methodology is about creating shared expectations and "social contracts" within your team, ensuring your codebase can gracefully evolve.
