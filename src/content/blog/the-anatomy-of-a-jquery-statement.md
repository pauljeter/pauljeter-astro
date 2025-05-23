---
title: "The Anatomy of a jQuery Statement"
description: ""
pubDate: 2012-03-26
categories: 
  - "jquery"
heroImage: "/images/jquery.jpg"
---

## The jQuery Alias

Let's start with the amazing little function that you gain access to when you include the jQuery library in your page. It simply goes by the name, jQuery. The jQuery library is contained inside of the jQuery namespace. Namespacing is a great way to ensure that we play nice with other JavaScript on the page, but it could get quite annoying to have to type the full jQuery name everytime you want to call a command. That's why jQuery gives us a shorter alias to access the library, $. Unfortunately, other JavaScript libraries also use the $ alias. We'll discuss this in a future post.

## Taking Apart the jQuery Statement

So you know how to call the jQuery function or it's alias, now let's look at the rest of the jQuery statement.

Every command is made up of four parts: the jQuery function, selectors, actions or methods, and parameters. First, we use a selector to select one or more elements on the page. Next, we choose an action to be applied to the element. We will explore many of the actions at our disposal as we dive further into the world of jQuery in future posts. And lastly, we will specify some parameters to define how we want jQuery to apply the action. As you're starting out, whenever you see some jQuery code, break it up into these components. This will make it easier to understand what the code is doing.

|   **Selector**   |   **Action**   |   **Parameters**   |
| --- | --- | --- |
|   jQuery(‘p’)   |   .css   |   (‘color’, ‘red’);   |
|   $(‘p’)   |   .css   |   (‘color’, ‘red’);   |

In this example, we have selected all of the paragraph tags. Then we chose the css action to modify the CSS properties of the paragraphs on the page. Then we passed the parameters to set the CSS color property to the value red. What will be the result? All of the paragraphs will now be red! The actions and parameters will get more complex as we go along our jQuery journey, but all commands will follow this basic pattern.

This is the first in a series of posts where we will explore and learn about the jQuery library. I hope that you will come back to find out more.
