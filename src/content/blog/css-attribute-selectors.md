---
title: "CSS Attribute Selectors"
description: ""
pubDate: 2013-12-06
heroImage: '/images/css.jpg'
categories: 
  - "css"
tags: 
  - "attributes"
  - "css"
  - "selectors"
  - "web-development"
---

Attribute selectors were introduced in CSS2, and CSS3 added a few more. An attribute selector will match elements on the basis of either the presence of an attribute, or the exact or partial match of an attribute value.

Attribute selectors are delimited by square brackets. The simplest form of an attribute selector consists of an attribute name surrounded by square brackets:

```
[href] {
  /* declarations */
}
```

This example selector matches any element that has an `href` attribute. It also contains an implied universal selector, and is equivalent to \*\[`href`\].

In another example:

```
a[href] {
  /* declarations */
}
```

This selector matches any a element that has an `href` attribute, so it matches a hypertext link, but not a named anchor.

Attribute selectors can also specify a value, or a partial value, to match. The values must be strings, in which case they're surrounded by single or double quotes, or identifiers, without quotes. All the examples below use strings.

### Case Sensitivity

The value specified in an attribute selector is case sensitive if the attribute value in the markup language is case sensitive. Thus, values for id and class attributes in HTML are case sensitive, while values for lang and type attributes are not.

It's not always easy to remember which HTML attributes are case sensitive and which aren't. It's usually best to assume that everything is case sensitive, but don't rely on it!

We can use the = operator to have an attribute selector match elements that have specific values:

```
input[type="submit"] {
  /* declarations */
}
```

This selector matches any input element that has a type attribute with a value equal to "submit".

### Default Attributes

Attribute selectors can only match attributes and values that exist in the document tree, and there's no guarantee that a default value specified in a DTD (or similar) can be matched. For instance, in HTML, the default value for a form element's `method` attribute is `"get"`, but you can't rely on a selector like `form[method="get"]` to select a form element with the start tag `<form action="comment.php">`.

### Attribute Selectors for IDs

Note that `[id="foo"]` isn't equivalent to `#foo`. Although both selectors would match the same element in HTML, there's a significant difference between their levels of specificity.

We can use the `|=` operator to cause an attribute selector to match elements which have an attribute containing a list of hyphenated words that begin with a specific value:

```
[hreflang|="en"] {
  /* declarations */
}
```

This example selector matches any element that has an `hreflang` attribute containing a value of "`en`", whether or not that value is followed by a hyphen and more characters. In other words, it matches `hreflang` attribute values of "`en`", "`en-US`", "`en-GB`", and so on. This selector syntax was intended to allow language subcode matches.

### Hyphen or No Hyphen?

All supporting browsers allow a hyphen to appear in the value in a selector like \[`hreflang|="en"`\]. It's unclear whether or not this is illegal, because the CSS specification doesn't contain any guidelines to help us deal with this situation.

We can use the ~= operator to make an attribute selector match elements that have an attribute that contains a list of space-separated words, one of which is the specified value:

```
[class~="warning"] {
  /* declarations */
}
```

This selector matches any HTML element with a `class` attribute that contains a space-separated list of words, one of which is`"warning"`. So it matches `<p class="warning">` and `<strong class="important warning">` and `<div class="warning highlight">`, but not `<p class="my-warning">` or `<ul class="warnings">`.

### Example

This selector matches all `input` elements with a `type` attribute that's equal to `"submit"` (in other words, submit buttons):

```
input[type="submit"] {
  /* declarations */
}
```
