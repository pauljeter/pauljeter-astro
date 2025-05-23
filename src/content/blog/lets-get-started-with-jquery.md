---
title: "Let’s get started with jQuery"
description: ""
pubDate: 2012-03-19
categories: 
  - "jquery"
heroImage: "/images/jquery.jpg"
tags: ['jQuery', 'Frameworks', 'JavaScript', 'JS', 'Libraries']
---

## **So What Is jQuery?**

 jQuery is a lightweight JavaScript library (or framework), that takes the headache out of having to write pure JavaScript in your websites. It has many powerful features built-in including (but not limited to): traversing the DOM, animations and effects, and simple AJAX techniques and methods.  I believe the [jQuery home page](http://jquery.com/ "jQuery") describes it best:

> _jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.  
> _

## **What Are Some Of The Benefits Of jQuery?**

Why would you even use a framework of library if there were no benefit that would come from using it? Let’s just touch the surface on some of the benefits and features of using the jQuery library.

- It reduces the amount of code that needs to be written compared to pure Javascript, which leads to less development time and more readable code.
- It is much easier to understand than scripting with pure Javascript.
- The documentation is extremely well organized and the community is very active.
- It makes using Ajax extremely easy.
- A wide range of plugins and extensions have been developed for jQuery to get the exact functionality you are looking for.
- It is the most adopted and used JavaScript framework/library.

## **How Do I Get Started?**

The first thing you need to do to get started with jQuery is visit the [jQuery download page](http://jquery.com/download/ "Download jQuery") and [download](http://jquery.com/download/ "Download jQuery") the latest version of jQuery. Once you have downloaded the jQuery library, simply upload the library to your server and link to in in the <head> section of your document as seen in the code below.

```
<script src="/jquery.js"></script>
```

You can also use a content delivery network (CDN) to host your jQuery code for you, which can net you faster load times, especially if the version of jQuery that you are using is already cached in your user’s browser. You can find out more on the [jQuery download page](http://jquery.com/download/ "Download jQuery").

Now that we have downloaded and properly linked to the jQuery library on our server, we can move onto our next piece of code, which will execute when the document is ready.

## **Is The Document Ready?**

To run our first jQuery script, we need to encapsulate all of our script inside a function. This function will execute any code contained inside when the document is ready. Let’s take a look at an example and then go over it in more detail.

```
$(document).ready(function() {
  // Code goes here
});
```

Here, we tell the browser to execute any code inside the function as soon as the DOM is ready. There are many reasons for doing this. First, by doing this we are completely separating our JavaScript from our HTML.  Second, we are not waiting for the page to load, but for the DOM to load completely. This ensures that we do not execute any code before the DOM is ready to deal with it.

For the lazy (I mean efficient) developers out there, you can shorten the above section of code to reflect the code below. Both behave the exact same way.

```
$(function() {
  // Code goes here
});
```

You now know how to link to the jQuery library and set up your _document.ready_ function, the last step is to actually write some of our jQuery code that will affect or manipulate our page in some manner. We'll dive more into this step in our next article.

## Check back for more!

I hope that this shor introduction to jQuery has sparked your interest in this wonderful library. Stay tuned for more jQuery tutorials, tricks, and tips! If you have any questions, comments, or suggestions, please let me know in the comments section below!
