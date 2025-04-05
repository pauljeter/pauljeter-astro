---
title: 'Getting Started with Foundation 5 by ZURB'
description: 'A simple guide to getting started with Foundation 5 by ZURB.'
pubDate: '2015-01-08'
heroImage: '/images/foundation-5.jpg'
---

Often, when you talk about front-end frameworks, Bootstrap, Foundation by ZURB, and uikit are usually the ones that are brought up.

A lot of people gravitate towards Bootstrap because of its ease of use, simple docs, great features, adoption in the industry, extensibility… I guess this list could go on and on.

I’ve always seen Foundation as an alternative but never looked into what features they offered and if they could be a viable alternative to Bootstrap to be honest. There wasn’t really a need to since Bootstrap did most of the things I needed from it.

Recently, however, ZURB has been talking about Foundation for Apps. The way they are looking at modern applications really makes sense and fills a growing need that modern websites need to feel more interactive like their mobile counterparts. Foundation for Apps consists of three main parts:

- The Grid
- Motion UI
- AngularJS Integration

As an example, ZURB is talking about Motion UI in the following gif. Websites that feel more interactive and friendly will be coming soon from them.

![Foundation Motion UI](/images/foundation-1.gif)

Also, their new grid definitely feels more like how I build Angular applications nowadays. Panels, sections, and columns galore.

These articles caught my attention because I like that ZURB is trying to innovate or at least move forward front-end frameworks (I also like their stylings a bit better than Bootstrap 3’s). So now here we are, I’ve taken a good look at what Foundation has to offer and have come away pleased and wondering why I haven’t looked before.

There is a ton to the Foundation website, and it can be a little overwhelming at first.

### Navigating the Site

![Foundation Homepage](/images/zurb-homepage-1012x500.png)

There are a lot of links in the header of the site and you can easily get lost in all of them (there’s a lot of great info there). To keep this simple, there are only three sections that are needed if you just want to get your feet wet and start developing with Foundation:

- [Develop or Develop -> Add-ons](https://foundation.zurb.com/templates.html)
- [Docs](https://foundation.zurb.com/docs.html) Getting Started link also goes here
- [Download](https://foundation.zurb.com/download.html) lets you download and customize for the parts you want

The main sections we’ll be looking at are Develop -> Add-ons and Docs.

### Installation

Looking through their docs, there are three different packages we can go into: **CSS**, **SASS**, and **Building an App**. For more advanced uses, Foundation comes with a CLI that you can download and install so that you get Foundation commands from the command line. We won’t be messing with that stuff today, just the CSS.

Downloading the Foundation CSS is all we have to do. We’ll get a sample site in index.html where we can test out CSS and JS features.

![Foundation Preview](/images/zurb-foundation-5-preview.png)

#### CSS Setup

To start up a Foundation site, we’ll need two CSS files: `normalize.css` and `foundation.css`. Those will be enough to get the classes we need and then we can add our own stylings in a custom stylesheet that we’ll call `app.css`:

```html
<link rel="stylesheet" href="css/normalize.css">
<link rel="stylesheet" href="css/foundation.css">
<link rel="stylesheet" href="css/app.css">    <!-- your custom styles -->
```

Now we have access to the classes that are necessary to build out all parts of Foundation. Let’s say we needed buttons. The syntax isn’t too far off of the Bootstrap way. You have `.button`, `.tiny`, `.small`, `.large`, `.radius`, `.round`, `.success`, and `.alert`. We could create buttons by writing:

```html
<a href="#" class="button tiny primary">Tiny Primary</a>  
<a href="#" class="button large success radius">Radius Success</a>
<a href="#" class="button large alert round">Rounded Alert</a>
```

#### JS Setup

To get the JavaScript going, we’ll need three things: `jquery.js`, `foundation.min.js`, and we’ll need to initialize Foundation like so:

```html
<script src="js/vendor/jquery.js"></script>
<script src="js/foundation.min.js"></script>
<script>
    $(document).foundation();
</script>
```
By adding that `$(document).foundation();` line, we’ll be able to define our JavaScript elements just by using **HTML5 data-attributes**. Here’s an example of the dropdown split button and the tabs:


#### Features

Take a look at ALL the features in one place. ZURB made the Kitchen Sink to show off all of Foundation 5’s goodness.

We won’t dive too far into many of these just yet. The CSS is easy enough (just copy and paste the classes), and we’ll be going more in depth into the grid, JavaScript components, and other fun features in separate articles.

### CSS Features

The thing that is great about Foundation is that it strives to be fully responsive. In this spirit, pretty much everything is defined using ems or rems. Even the media queries and widths of the grid system use ems. This is a great practice since it ensures you are starting your sites with a responsive… umm foundation.

The CSS classes that come with Foundation are easy enough to learn and understand. Just read through the docs and ZURB’s great examples to see how to create buttons and whatnot. Here’s a quick list of some CSS features.

- Media Queries
- Visibility Classes: Hiding and Showing things based on device size (Foundation is mobile first). There’s even classes to detect landscape/portrait and touch/nontouch devices.
- Grid
- Utility Classes: Floats, Rounded and Border Radius on Buttons, Text Aligning
- Side Nav, Sub Nav, Breadcrumbs, Pagination
- Thumbnails
- Flex Video: Let your browser automatically scale video objects!
- Forms
- Buttons and Button Groups
- Typography, Lists, Labels, Blockquotes, and more
- Progress Bars
- Tables

Here’s a little showcase of some unique features:

#### Icon Bar
![Icon Bar](/images/icon-bar.jpg)

#### Switches
![Switches](/images/switches.jpg)

#### Pricing Tables

I wish the syntax for this was a bit more semantic, but it’s still cool nonetheless.

![Pricing Tables](/images/pricing-tables.jpg)


That’s a giant list. The docs can definitely show all that off best, so head on over and check out the great CSS features. Foundation is very polished in all of its CSS elements and I like the additions of pricing table, icon bar, switches, and some useful visibility and utility classes that could be used often.

### JS Features

The JavaScript features that come with Foundation are great as well. One of the big JS features is the built in off-canvas menus. We’ve detailed how to create off-canvas menus but it’s good to have a solution built into the framework that you’re using.

#### Off Canvas Menus

Here’s a quick list of the other JS features:

- Interchange Responsive Content: Switch out HTML content based on browser size
- Off Canvas
- Top Bar, Sticky Nav
- Clearing Lightbox: Good looking implementation of a lightbox with gallery
- Range Sliders
- Abide Validation
- Split Buttons, Dropdown Buttons
- Modals, Alerts, Tooltips
- Joyride: Awesome feature to create guided tours around your site
- Dropdowns, Accordion, Tabs
- Equalizer: Create equal height content!
- Range Sliders

### Should You Use Foundation 5?

Foundation is a solid framework that has been tested, has solid backing in ZURB, and continues to innovate (can’t stress how much I like their Motion UI and new grid stuff). The syntax is easy to learn and get started with. There’s no reason not to give it a try. Just spin up a CodePen and play around with the features.

The addition of visibility classes and the work they’ve done with accessiblity are great additions as well. Take a look through their docs and see what you find. I think you walk away impressed. There’s just so many features and components with ideas that make sense (Interchange is a big one).

### Want More Foundation?

Here are some more articles to get you going with Foundation:

- [Foundation 5 Features that Bootstrap Doesn’t Have](/blog/foundation-5-features-that-bootstrap-doesnt-have)
- [Cheat Sheet for Comparing Bootstrap and Foundation CSS Classes](/blog/cheat-sheet-for-comparing-bootstrap-and-foundation-css-classes)