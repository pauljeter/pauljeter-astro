---
title: 'Foundation 5 Features That Bootstrap Doesn't Have'
description: 'A comparison of features between Bootstrap 3 and Foundation 5 by ZURB.'
pubDate: '2015-01-15'
heroImage: '/images/foundation-and-bootstrap.jpg'
---

There are many differences and similarities between Bootstrap and Foundation. The biggest similarity is that they are both great front-end frameworks that can be used to build out awesome applications. They come with lots of great features, are mobile first, responsive, and customizable, and extensible.

I am a big user of Bootstrap and love the great features it provides. Recently, I took a look at Foundation 5's features and how to use it. It's a great framework that has a few cool things to offer that default Bootstrap does not. Here's a look through some of the cool features you can find in Foundation that aren't in Bootstrap.

### CSS Features
#### EM Based
Everything about Foundation works to be "the most advanced responsive front-end framework". In this spirit, they have used ems for everything from font-sizes to media query breakpoints.

#### Base Classes
Bootstrap prefixes its classes with the type of class that it is (ie .text-success, .img-circle). Foundation comes with a set of universal classes to specify colors and shape. These apply to a variety of things including buttons, alerts, panels, and more.

The classes are: tiny, small, large, secondary, success, alert, radius, and round. Here's a few examples applied to buttons.



#### Switches
All CSS switches to spice up your forms. These don't require JavaScript at all.


#### Visibility Classes
Bootstrap has classes for showing and hiding elements based on screen size. Foundation also has classes to show and hide elements, but they provide a few cool classes for showing and hiding based on portrait vs landscape and touch vs nontouch devices.

The classes are:

```html
<!-- show or hide for portrait vs landscape -->
<p class="panel">
  <strong class="show-for-landscape">You are in landscape orientation.</strong>
  <strong class="show-for-portrait">You are in portrait orientation.</strong>
</p>

<!-- show or hide based on touch vs nontouch -->
<p class="panel">
  <strong class="show-for-touch">You are on a touch-enabled device.</strong>
  <strong class="hide-for-touch">You are not on a touch-enabled device.</strong>
</p>
```

#### Pricing Tables
Having prebuilt pricing tables is good to have since those can be a complicated thing to style up and get looking good.


### JavaScript Features
The JavaScript features that Foundation comes with help fill a lot needs that developers could have. Instead of going around searching for different jQuery plugins for a specific feature, it's nice to have them built into the framework you're using.

#### Interchange
Interchange is a feature that uses media queries to dynamically load responsive content. What this means is that you can specify what HTML you want to show for mobile, tablet, and desktop sites. I know that we have this ability using the visibility classes, but using those classes just applies display:none;. This doesn't stop the content from being loaded so this could mean that you have desktop components loading and slowing down your mobile users.

Take a look at the Interchange docs and see how you can dynamically load a Google map for desktop users and a photo for mobile users.

#### Joyride
Joyride helps to create those site tours (some people call them wizards I believe) that we see when signing up for our favorite websites or applications.

#### Off Canvas
An often seen feature that is also included in the framework.

#### Lightbox
The Clearing Lightbox offers a great looking lightbox with gallery and caption features.

#### Range Sliders
Range Sliders are nice sliders that let you build out draggable sliders.

#### Equalizer
The Equalizer feature ensures that elements of your site will have the same height. It'll be nice when flexbox support comes to all browsers, but until then, JavaScript plugins like this will be needed.

### Conclusion
Remember, this is not to say that Foundation is better than Bootstrap. Bootstrap also has features that you won't find in Foundation. This is just a look at some cool features that you can find in Foundation and we recommend trying out multiple front-end frameworks (like you would programming language or server-side frameworks) to find out what works best for your tastes or current project.

### Want More Foundation?
Here are some more articles to get you going with Foundation:

- [Getting Started with Foundation 5 by ZURB](/blog/getting-started-with-foundation-5-by-zurb)
- [Cheat Sheet for Comparing Bootstrap and Foundation CSS Classes](/blog/cheat-sheet-for-comparing-bootstrap-and-foundation-css-classes)