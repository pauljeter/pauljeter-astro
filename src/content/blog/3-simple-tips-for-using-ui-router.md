---
title: '3 Simple Tips for Using UI-Router'
description: 'A look at three features that UI-Router provides that you might find useful when building your own applications.'
pubDate: '2015-06-15'
heroImage: '/images/angularjs-2.jpg'
---

Today we’ll be going over three features that UI-Router provides that you might find useful when building your own applications.

### Linking To States
Angular provides the `ngHref` directive which allows us to bind variables to URLs. UI-Router provides us with `ui-sref` which allows us to link to states. This is different than linking to a normal URL. When using UI-Router you want to link to a state, not a URL.

#### Examples
Let’s say we have a state like so:

```javascript
$stateProvider

    .state('party', {
        url: '/party',
        template: '<h1>This Is A State</h1>'
    });
```

Now to link to it in one of our views:

```html
<a ui-sref="party">Go To Party</a>
```

This will turn into `<a href="/party" ui-sref="party">Go To Party</a>`in our browser. Notice how the href is generated for us.

### Using URL Parameters with States
When we have parts of our application where we want to pass URL parameters to, we can pass those into our states.

#### Defining a State with URL Parameters
Here is how we define states with parameters:

```javascript
$stateProvider

    .state('partyDetail', {
        url: '/party/:partyID/:partyLocation'
    });
```

You can also define these by using `{partyID}/{partyLocation}`. Now we have a state that uses two parameters.

#### Linking to a State with URL Parameters
Now this is how we will link to it in our views. We treat it like a function and will pass in each parameter through

`ui-sref`. For this example, let’s say that we have some variables that we will want to use: id with a value of 5 and `location` with a value of las-vegas.

```html
<a ui-sref="partyDetail({ partyID: id, partyLocation: location })">See the Party</a>
```

This will create the href for our link and will look like: `<a href="/party/5/las-vegas">See the Party</a>.`

### Accessing URL Parameters
We will probably need to use these in our controllers so let’s go ahead and grab those using UI-Router’s

`$stateParams`. For this example, we’ll just add a controller directly into our route.

```javascript
$stateProvider

    .state('partyDetail', {
        url: '/party/:partyID/:partyLocation',
        controller: function($scope, $stateParams) {
            // get the id
            $scope.id = $stateParams.partyID;

            // get the location
            $scope.location = $stateParams.partyLocation;   
        }
    });
```

### Adding Classes Based on Current State
When users are browsing our application or site, sometimes we want to highlight things to let them know where they are. A good example of this is highlighting navigation items if they are currently on that page. UI-Router provides an easy way to add classes if the state matches the current state. All we have to do is use

`ui-sref-active`. For this example, we have states called home, about and contact. If we wanted to add an active class to each if the state is active, we just do the following:

```html
<ul>
    <li><a ui-sref="home" ui-sref-active="active">Home</a></li>
    <li><a ui-sref="about" ui-sref-active="active">About</a></li>
    <li><a ui-sref="contact" ui-sref-active="active">Contact</a></li>
</ul>
```

Now if the current state matches the state in

`ui-sref`, the class provided in `ui-sref-active` will activate. Then we can style that to our heart’s content.

### Conclusion
Hopefully these tips will help you build better Angular applications. Sound off in the comments if you have any great tips or any questions about UI-Router.

