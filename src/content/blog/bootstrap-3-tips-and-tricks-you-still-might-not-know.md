---
title: "Bootstrap 3 Tips and Tricks You Still Might Not Know"
description: ""
pubDate: 2014-11-4
categories: 
  - "javascript-summit"
tags: 
  - "bootstrap"
  - "css"
  - "tips-and-tricks"
  - "web-development"
heroImage: '/images/bootstrap-3.jpg'
---

Bootstrap 3 is awesome. Not only does is provide all the basics of a front-end framework, but it also has a ton of helpers to speed up development. These helpers can be used to rapidly prototype something out or to build an extremely strong and reliable front-end foundation for a longer-term application. 

Optionally Remove the Gutter Padding from Columns
Bootstrap lets you customize and compile your own build based on your needs. This is anything from colors, container sizes, and to gutter padding size. However, sometimes you’ll come across an instance where you just want a single row with no padding. Most cases you’ll just individually select the column and kill off the padding with CSS. However, you can build your own utility class helper to do this on the fly. This utility class will cover all column sizes and still supports full responsiveness. Here’s the CSS snippet:

```css
.no-gutter > [class*='col-'] {
    padding-right:0;
    padding-left:0;
}
```

And here’s how you can use it in your HTML:

```html
<div class="row no-gutter">
    <div class="col-md-4">
        ...
    </div>
    <div class="col-md-4">
        ...
    </div>
    <div class="col-md-4">
        ...
    </div>
</div>
```

And here’s how you can use it in your HTML:

```html
<div class="row no-gutter">
    <div class="col-md-4">
        ...
    </div>
    <div class="col-md-4">
        ...
    </div>
    <div class="col-md-4">
        ...
    </div>
</div>
```

Custom Container Sizes
Like it or not, sometimes you’ll be working on a design that doesn’t follow a grid system or a designer who likes to push the boundaries farther and use different grid column sizes on different rows throughout a page and / or site. Bootstrap columns automatically fill to it’s parent container. So if you need a smaller container or a larger container, you can easily extend the Bootstrap core and make your own container classes. Here’s an example:

```css  
@media (min-width: 768px) {
    .container-small {
        width: 300px;
    }
    .container-large {
        width: 970px;
    }
}
@media (min-width: 992px) {
    .container-small {
        width: 500px;
    }
    .container-large {
        width: 1170px;
    }
}
@media (min-width: 1200px) {
    .container-small {
        width: 700px;
    }
    .container-large {
        width: 1500px;
    }
}
```

Now the only thing you need to worry about is overflow issues if say a container you made is larger then the device window. For example with the .container-large class, if a user has a browser window of 1200px, it will create this nasty overflow issue. Here’s the fix for that.

```css
.container-small, .container-large {
    max-width: 100%;
}
```

Use Heading Classes to Save Time and Stay Semantic
A design sometimes will have elements that don’t always match best practice for having semantic markup. What I mean by this is usually your h1 tag is followed by an h2 and so on. This isn’t necessarily a bad thing when this happens, it’s just something to watch out for because at the end of the day, one of the most important things to make sure of is that your markup is structured in a way that is friendly to read for Google and other Bots.

You can swap out Headings styles with different classes. Take a look at the example code below to see it in action:

```html
<h1 class="h2">Heading 1 that looks like Heading 2</h1>
<h2 class="h4">Heading 2 that looks like Heading 4</h2>
<h3 class="h1">Heading 3 that looks like Heading 1</h3>
```


Responsive Video Embeds that Maintain Aspect Ratio
When Bootstrap 3.2 came out, it came out with an additional helper class to make it easier to make iframes (like YouTube embeds) responsive while maintaining a certain aspect ratio. It’s extremely easy to use these, just add the following code to your markup:

```html
<!-- 16:9 aspect ratio -->
<div class="embed-responsive embed-responsive-16by9">
    <iframe class="embed-responsive-item" src="//www.youtube.com/embed/ePbKGoIGAXY"></iframe>
</div>

<!-- 4:3 aspect ratio -->
<div class="embed-responsive embed-responsive-4by3">
    <iframe class="embed-responsive-item" src="//www.youtube.com/embed/ePbKGoIGAXY"></iframe>
</div>
```

Notice how the iframe doesn’t include frameborder="0". This is because Bootstrap will actually normalize any ugly outlines for you with this helper class.


Responsive Utility Classes Need a Display Property
With Bootstrap 3.2 being released, they updated the way responsive utility classes work. Normally you would just assign .visible-xs, .visible-sm, .visible-md, and .visible-lg to hide or show certain elements at different device widths. Now, you actually have to specify a “state” as well of either block, inline, or inline-block. This maximizes your control, but if you’re confused on which on to use, just use block. Here’s some examples:

```css
/* With * being xs, sm, md, or lg */
.visible-*-block {}
.visible-*-inline {}
.visible-*-inline-block {}
```

Extend the Class, Don’t Override It
I often see front-end code where developers completely override Bootstrap styles to customize buttons and other elements rather than extending the existing classes. This gets messy real fast. It’s much easier to maintain if you just extend the existing classes. For example, let’s make a completely flat and yellow button called .btn-yellow to demo the principle.

Heads Up! Using a color as a class name is probably a bad idea and can make maintaining your CSS harder than it needs to be. The example does it, but you should do something like btn-custom-name.

```css
.btn-yellow {
  background: rgb(250, 255, 140);
  color: #574500;
  border: none;
  -moz-box-shadow: none !important;
  -webkit-box-shadow: none !important;
  box-shadow: none !important; /* !important tags aren't necessarily always bad */
}
.btn-yellow:hover, .btn-yellow:focus {
  background: rgb(252, 255, 179);
}
.btn-yellow:active {
  background: rgb(247, 255, 71);
}
```

This way you can still use things like .btn-lg or .btn-block to customize your buttons. Now, I’ll also make a class called .btn-xxl:

```css
.btn-xxl {
  padding: 20px 26px;
  font-size: 35px;
  border-radius: 8px;
}
```

Building a base CSS by extending the classes can prove to be extremely helpful in the long run and can really speed up your front-end development.

```css
* { box-sizing: border-box; }
```

My favorite thing about Bootstrap 3 versus 2 is that it adopted the new box-sizing: border-box property for all elements and pseudo-elements (:before and :after). This might be more obvious to some, but what this does is changes the way the CSS box-model works. When this is enabled the width and height properties include the padding and border, but not the margin. In laymen terms, if you add padding, your element isn’t going to grow in size. Instead, the element’s contents gets pushed closer and closer towards the center of the box.

Bootstrap 2 didn’t use this method, and I imagine people people who recently switch will be thrown off by this since it goes against how most people are taught CSS in the first-place. After you get used to it though, it starts to make responsive web development a lot easier and will probably be your new default even without Bootstrap. I think the idea to do it this way was first introduced by Paul Irish from this post.

Conclusion
It’s all about using the right tool for the job. Sometimes Bootstrap will be a good choice for you, and other times it won’t be. The important thing to remember is that Bootstrap was built with extensibility in mind. You can pick and choose what pieces to use and which parts to use or build off from based on your needs. It’s not going to do all your front-end work for you, but it sure will make front-end development a whole lot easier.