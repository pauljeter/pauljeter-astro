---
title: "Useful CSS Selectors You Might Not Know About"
description: "CSS has some great selectors built-in that many developers aren't aware of"
pubDate: 2013-11-15
heroImage: '/images/css.jpg'
categories: 
  - "css"
tags: 
  - "css"
  - "selectors"
  - "web-development"
---

CSS has some great selectors built-in that many developers aren't aware of. Knowing these can significantly simplify styling your webpages. You can select even and odd elements, first and last children, siblings, and more.

In this article, we'll explore some lesser-known CSS selectors and demonstrate how to use them effectively. We won't dive into common selectors like IDs and classes; instead, we'll focus on selectors that often fly under the radar.

Let's get started!

### First Line and First Letter Selectors

- **`:first-letter`** - Style just the first letter in a paragraph.
```css
p:first-letter {
  font-size: 2em;
  font-weight: bold;
}
```

- **`:first-line`** - Style just the first line in a paragraph.
```css
p:first-line {
  color: red;
}
```

### Before and After Pseudo Elements

- **`:before`** - Add elements before the current element.
```css
p:before {
  content: "Note: ";
  color: blue;
}
```

- **`:after`** - Add elements after the current element.
```css
p:after {
  content: " ★";
  color: gold;
}
```

### Sibling and Child Selectors

- **Child Selector `>`** - Selects direct child elements only (not nested).
```css
body > p {
  font-weight: bold;
}
```

- **Adjacent Sibling Selector `+`** - Selects the element immediately following a specific element.
```css
h1 + p {
  font-size: 18px;
}
```

- **General Sibling Selector `~`** - Selects all siblings after a specific element.
```css
h1 ~ pre {
  background-color: #f0f0f0;
}
```

### Target Pseudo Class `:target`

Use this to style an element targeted by a URL hash.

**Example:**  
URL: `http://example.com/about.html#thebox`

HTML:
```html
<div id="thebox">This content will be styled.</div>
```

CSS:
```css
*:target {
  border: 2px solid red;
  background-color: yellow;
}
```

This is helpful for highlighting specific sections or comments linked via URLs.

### :nth-child Pseudo Classes

- **First or last elements**
```css
tr:first-child { background-color: yellow; }
tr:last-child { background-color: green; }
```

- **Odd or even elements**
```css
tr:nth-child(odd) { background-color: #f9f9f9; }
tr:nth-child(even) { background-color: #e9e9e9; }
```

- **Specific patterns**
  - Every 9th, 19th, 29th element
```css
tr:nth-child(10n-1) {
  color: red;
}
```

  - First 6 rows
```css
tr:nth-child(-n+6) {
  font-weight: bold;
}
```

### Attribute Selectors

- **Contains a specific value (`~=`)**
```css
a[rel~="copyright"] {
  font-style: italic;
}
```

- **Begins with a value or dash (`|=`)**
```css
a[hreflang|="en"] {
  color: green;
}
```
Selects `en`, `en-US`, `en-GB`, etc.

- **Begins with a specific string (`^=`)**
```css
img[src^="images/"] {
  border: 1px solid blue;
}
```

- **Ends with a specific string (`$=`)**
```css
a[href$=".html"] {
  text-decoration: underline;
}
```

### And So Much More!

CSS offers many additional powerful selectors such as `:nth-of-type`. To explore all available selectors, visit the official [W3C CSS Selector Reference](https://www.w3.org/TR/selectors-3/).
