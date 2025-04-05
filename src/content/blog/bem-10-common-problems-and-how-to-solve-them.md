---
title: 'BEM: 10 Common Challenges and How to Solve Them'
description: 'A practical guide to overcoming common issues when adopting the BEM CSS methodology in your projects, ensuring scalable and maintainable CSS.'
pubDate: '2017-06-26'
heroImage: '/images/bem.jpg'
category: 'CSS'
tags: ['BEM', 'CSS', 'Frontend Development']
---

If you're exploring BEM (Block, Element, Modifier) methodology or already integrating it into your workflow, you've likely encountered challenges along the way. While BEM offers powerful benefits, its syntax can initially seem intimidating. Here, I’ll outline 10 common issues developers face when adopting BEM and provide solutions to each.

## 1. How to Handle Nested Elements ("Grandchild Selectors")

BEM class naming shouldn’t reflect your entire DOM structure. Using multiple element-level selectors quickly leads to unreadable class names:

**Avoid this:**
```html
<div class="c-card">
  <div class="c-card__header">
    <h2 class="c-card__header__title">Title</h2>
  </div>
</div>
```

**Do this instead:**
```html
<div class="c-card">
  <div class="c-card__header">
    <h2 class="c-card__title">Title</h2>
  </div>
</div>
```

Keep your selectors shallow. Each element should directly reference the block (`c-card`), regardless of nesting depth. If you find yourself frequently nesting deeper, reconsider your component structure.

## 2. Should You Use Namespaces?

Yes! Namespacing significantly improves code readability. I follow a namespacing strategy inspired by Harry Roberts:

| Type             | Prefix  | Example               | Purpose                                              |
| ---------------- | ------- | --------------------- | ---------------------------------------------------- |
| Component        | `c-`    | `c-card`              | Standalone UI elements                               |
| Layout           | `l-`    | `l-grid`              | Purely structural, no cosmetics                      |
| Helper           | `h-`    | `h-hide`              | Utility classes for positioning, visibility, etc.    |
| State            | `is-`, `has-` | `is-active`, `has-loaded` | Dynamic states of components                 |
| JavaScript hooks | `js-`   | `js-tabs`             | Classes used solely for JavaScript hooks             |

This clear distinction aids communication and code management.

## 3. Naming Wrapper Elements

Often, components require wrappers. Instead of inventing overly specific wrappers, I abstract layout into reusable modules:

**Example:**
```html
<ul class="l-grid">
  <li class="l-grid__item">
    <div class="c-card">...</div>
  </li>
  <li class="l-grid__item">
    <div class="c-card">...</div>
  </li>
</ul>
```

If no layout module applies, use simple, consistent terms like `l-cards-container` or `l-cards-list`.

## 4. Handling Cross-Component Styles

Sometimes, a component’s appearance changes slightly based on its parent context. Rather than creating parent-dependent classes (`c-card__button`), use reusable modifiers:

```html
<button class="c-button c-button--small c-button--rounded">Click me</button>
```

This maintains component independence and avoids specificity issues.

## 5. Deciding Between Modifier or New Component

When styles differ slightly, deciding between a modifier and a new component can be tricky. If your modifiers become overly complex or reset large chunks of base styles, it’s usually a sign to break out a new component.

Consult team members to determine where component boundaries should lie.

## 6. Handling States in BEM

State hooks can be tricky. I prefer independent state classes (`is-active`) rather than component-specific ones (`c-card--is-active`) because it simplifies JavaScript interactions:

```html
<div class="c-card is-active">...</div>
```

## 7. When to Avoid Adding Classes to Elements

I add classes to every element that needs unique styling within a component. Unstyled elements (like simple `<p>` tags) often remain classless unless specifically styled by the component.

Although this might initially feel verbose, it ensures components remain isolated and reliable.

## 8. Properly Nesting Components

Avoid deep, component-specific nesting. Instead, extract reusable components and layout modules:

**Avoid:**
```html
<ul class="c-card__checklist">
  <li class="c-card__checklist__item">...</li>
</ul>
```

**Prefer:**
```html
<ul class="l-list">
  <li class="l-list__item">
    <div class="c-checkbox">...</div>
  </li>
</ul>
```

This approach promotes reuse and clear structure.

## 9. Are Too Many Classes Bad?

Multiple classes per element are common with BEM:

```html
<button class="c-button c-button--primary c-button--large is-active">Click me</button>
```

While not always visually appealing, multiple explicit classes clearly indicate the element’s purpose.

If this feels excessive, consider alternative methods like combined classes (e.g., `.c-button--primary-large`), though this sacrifices modular flexibility.

## 10. Responsive Component Changes

Sometimes, a component changes type responsively (e.g., dropdown to tabs). Harry Roberts recommends responsive suffixes for clarity:

```html
<ul class="c-dropdown@small-screen c-tabs@large-screen">...</ul>
```

In CSS, remember to escape the `@` symbol:

```css
.c-dropdown\@small-screen { /* styles */ }
```

This clearly communicates responsive intent without confusion.

## Final Thoughts

BEM significantly improved my workflow over the years, providing a scalable framework for building modular UI. These common challenges reflect typical hurdles when adopting BEM, but with thoughtful implementation and best practices, BEM can transform your CSS into maintainable, clear, and collaborative code. Give it a try—it just might become your lifesaver too!
