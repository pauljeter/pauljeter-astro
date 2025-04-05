---
title: "CSS3 Attribute Selectors"
description: ""
pubDate: 2013-12-13
heroImage: '/images/css3.jpg'
categories: 
  - "css"
tags: 
  - "attributes"
  - "css"
  - "front-end"
  - "selectors"
  - "web-development"
---

CSS3 defines three new attribute selector variations. These selectors give us the ability to make partial matches to attribute values—we can match strings at the start, end, or anywhere within an attribute value.

We can use the ^= operator to cause an attribute selector to match elements that have an attribute containing a value that starts with the specified value:

```
a[href^="http:"] {
  /* declarations */
}
```

This example matches a elements that have an href attribute value which starts with the characters “http:”.

Using the $= operator, an attribute selector can match elements that have an attribute which contains a value ending with the specified value:

```
img[src$=".png"] {
  /* declarations */
}
```

This example matches a elements that have an href attribute value which starts with the characters “http:”.

Using the $= operator, an attribute selector can match elements that have an attribute which contains a value ending with the specified value:

```
div[id*="foo"] {
  /* declarations */
}
```

This example matches div elements whose id attribute value contains the characters “foo”.
