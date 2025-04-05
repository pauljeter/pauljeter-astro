---
title: 'Pretty URLs in AngularJS: Removing the Hashtag'
description: 'A guide to removing the hashtag from AngularJS URLs.'
pubDate: '2015-03-26'
heroImage: '/images/angularjs-2.jpg'
---

By default, AngularJS will route URLs with a hashtag.

For example:

- `http://example.com/`
- `http://example.com/#/about`
- `http://example.com/#/contact`

It is very easy to get clean URLs and remove the hashtag from the URL.

There are **2 things** that need to be done.

1. Configuring $locationProvider
2. Setting our base for relative links

### $location Service
In Angular, the `$location` service parses the URL in the address bar and makes changes to your application and vice versa.

I would highly recommend reading through the official Angular $location docs to get a feel for the $location service and what it provides.

### $locationProvider and html5Mode
We will use the `$locationProvider` module and set `html5Mode` to true.

We will do this when defining your Angular application and configuring your routes.

```javascript
angular.module('jeter', [])
    
    .config(function($routeProvider, $locationProvider) {

        $routeProvider
            .when('/', {
                templateUrl : 'partials/home.html',
                controller : mainController
            })
            .when('/about', {
                templateUrl : 'partials/about.html',
                controller : mainController
            })
            .when('/contact', {
                templateUrl : 'partials/contact.html',
                controller : mainController
            });
    
        // use the HTML5 History API
        $locationProvider.html5Mode(true);
    });
```

**What is the HTML5 History API?** It is a standardized way to manipulate the browser history using a script. This lets Angular change the routing and URLs of our pages without refreshing the page. For more information on this, here is a good [HTML5 History API Article](https://developer.mozilla.org/en-US/docs/Web/API/History_API).

Setting `<base>` For Relative Links
To link around your application using relative links, you will need to set a `<base>` in the `<head>` of your document.

```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">

    <base href="/">
</head>
```

There are plenty of other ways to configure this and the HTML5 mode set to true should automatically resolve relative links. This has just always worked for me. If your root of your application is different than the url (for instance `/my-base`, then use that as your base.)

### Fallback for Older Browsers
The `$location` service will automatically fallback to the hashbang method for browsers that do not support the HTML5 History API.

This happens transparently to you and you won’t have to configure anything for it to work. From the Angular $location docs, you can see the fallback method and how it works.

![hashbang_vs_regular_url](/images/hashbang_vs_regular_url.jpg)

### Conclusion
This is a simple way to get pretty URLs and remove the hashtag in your Angular application. Have fun making those super clean and super fast Angular apps!