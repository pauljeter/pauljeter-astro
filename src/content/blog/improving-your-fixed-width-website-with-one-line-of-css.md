---
title: "Improving your fixed-width website with one line of CSS"
description: ""
pubDate: 2013-11-30
heroImage: '/images/css.jpg'
---

With the age of mobile and responsive websites, more and more websites have fluid layouts. I personally feel it's becoming a standard amongst front-end developers to be developing with percentages or "em" units over pixels when possible; however, occasionally, the CSS can get mixed between fluid and fixed and create unexpected errors in the layouts especially when resizing the browser.

The common errors I often see can be reproduced when:

- The browser width is less than the width of the largest container and a user scrolls to the right.
- A fixed header or fixed element doesn't scroll horizontally with the rest of the website.
- Fluid containers on a fixed layout website causing layout issues when resizing the browser.
- 100% width size of a div or container is of the viewport and not the container.
- If your fixed-width website is having layout issues when resizing the browser, being at different viewport sizes, or when scrolling horizontally, a quick-fix CSS trick is to add:

Quick and easy fix for fixed-width layout resize issues

```css
html {
    /* Size of largest container or bigger */
    min-width: 1080px;
}
```

