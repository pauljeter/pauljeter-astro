---
title: "What is a Router?"
description: ""
pubDate: 2013-11-07
heroImage: '/images/digging-into-backbone.jpg'
categories: 
  - "backbonejs"
tags: 
  - "backbonejs"
  - "frameworks"
  - "javascript"
  - "js"
  - "libraries"
  - "routers"
---

Web applications often provide linkable, bookmarkable, shareable URLs for important locations in the app. Until recently, hash fragments (#page) were used to provide these permalinks, but with the arrival of the History API, it's now possible to use standard URLs (/page). Backbone.Router provides methods for routing client-side pages, and connecting them to actions and events. For browsers which don't yet support the History API, the Router handles graceful fallback and transparent translation to the fragment version of the URL.

During page load, after your application has finished creating all of its routers, be sure to call Backbone.history.start(), or Backbone.history.start({pushState: true}) to route the initial URL.

```
<script>
    var AppRouter = Backbone.Router.extend({
        routes: {
            "*actions": "defaultRoute" // matches http://example.com/#anything-here
        }
    });
    // Initiate the router
    var app_router = new AppRouter;

    app_router.on('route:defaultRoute', function(actions) {
        alert(actions);
    })

    // Start Backbone history a necessary step for bookmarkable URL's
    Backbone.history.start();

</script>
```

## Dynamic Routing

Most conventional frameworks allow you to define routes that contain a mix of static and dynamic route parameters. For example you might want to retrieve a post with a variable id with a friendly URL string. Such that your URL would look like "http://example.com/#/posts/12". Once this route was activated you would want to access the id given in the URL string. This example is implemented below.

```
<script>
    var AppRouter = Backbone.Router.extend({
        routes: {
            "posts/:id": "getPost",
            "*actions": "defaultRoute" // Backbone will try match the route above first
        }
    });
    // Instantiate the router
    var app_router = new AppRouter;
    app_router.on('route:getPost', function (id) {
        // Note the variable in the route definition being passed in here
        alert( "Get post number " + id );   
    });
    app_router.on('route:defaultRoute', function (actions) {
        alert( actions ); 
    });
    // Start Backbone history a necessary step for bookmarkable URL's
    Backbone.history.start();

</script>
```

## Dynamic Routing Cont. ":params" and "\*splats"

Backbone uses two styles of variables when implementing routes. First there are ":params" which match any URL components between slashes. Then there are "_splats" which match any number of URL components. Note that due to the nature of a "_splat" it will always be the last variable in your URL as it will match any and all components.

Any "\*splats" or ":params" in route definitions are passed as arguments (in respective order) to the associated function. A route defined as "/:route/:action" will pass 2 variables ("route" and "action") to the callback function. (If this is confusing please post a comment and I will try articulate it better)

Here are some examples of using ":params" and "\*splats"

```
     routes: {
        
            "posts/:id": "getPost",
            // <a href="http://example.com/#/posts/121">Example</a>
            
            "download/*path": "downloadFile",
            // <a href="http://example.com/#/download/user//hey.gif">Download</a>
            
            ":route/:action": "loadView"
            // <a href="http://example.com/#/dashboard/graph">Load Route/Action View</a>
            
        },
        
        app_router.on('route:getPost', function( id ){ 
            alert(id); // 121 
        });
        app_router.on('route:downloadFile', function( path ){ 
            alert(path); // user//hey.gif 
        });
        app_router.on('route:loadView', function( route, action ){ 
            alert(route + "_" + action); // dashboard_graph 
        });
```

That's it! Now get out there and start writing your Backbone.js apps.

### Digging into Backbone.js series:

- [What is Backbone.js?](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-backbonejs/ "What is BackboneJS?")
- [Installing Backbone.js](http://www.pauljeter.net/web-development/javascript/backbonejs/installing-backbonejs/ "Installing BackboneJS")
- [Models](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-model/ "What is a Model?")
- [Collections](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-collection/ "What is a Collection?")
- [Views](http://www.pauljeter.net/web-development/javascript/backbonejs/what-is-a-backbonejs-view/ "What is a View?")
- Routers
