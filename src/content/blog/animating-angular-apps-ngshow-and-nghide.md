---
title: 'Animating Angular Apps: ngShow and ngHide'
description: 'A guide to animating ngShow and ngHide directives in AngularJS.'
pubDate: '2015-02-28'
heroImage: '/images/angularjs-2.jpg'
---

### Introduction
Angular single page applications can be interactive and beautiful. The animations that can be used in Angular apps can help create the impression that it is a native phone or tablet application. We can bring animation to our Angular applications using the awesome ngAnimate module.

We’ve looked at how ngAnimate can help animate ngView. Today we’ll look at the simple way we can animate ngShow and ngHide directives.


### The Technique
ngAnimate adds CSS classes when certain things change in your application. To explain this further, when animating ngView, components enter and leave your application. ngAnimate adds the `.ng-enter` and `.ng-leave` classes. All we have to do is style (transitions or animations) to these using CSS classes.

#### ngShow and ngHide Classes
For ngShow and ngHide, the classes that are added are `.ng-hide-add` and `.ng-hide-remove`.

Note that `.ng-show` isn’t one of the classes.

We will have two buttons that will toggle show/hide their respective images.

We’ll just need an HTML file (`index.html`), a CSS file (`style.css`), and a JS file (`app.js`) to setup our Angular application. Let’s get our HTML and JS files going so we can focus on the CSS file. The CSS file is where the magic happens.

#### Setting Up Angular Application
Here is our JavaScript where we define our Angular application.

```javascript
// create our module and inject ngAnimate into it
angular.module('animateApp', ['ngAnimate'])

.controller('mainController', function($scope) {
  
  // set the default states for lions and cranes
  $scope.lions = false;
  $scope.cranes = false;
});
```

#### HTML
Now we have to apply our Angular app to our site. Here is our HTML:

```html
<!DOCTYPE html>
<html>
<head>
  <!-- CSS (load bootstrap from CDN) -->
  <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
  <link rel="stylesheet" href="style.css">
  
  <!-- JS (load angular and angular-animate from CDN) -->
  <script src="//ajax.googleapis.com/ajax/libs/angularjs/1.2.19/angular.min.js"></script>
  <script src="//cdnjs.cloudflare.com/ajax/libs/angular.js/1.2.20/angular-animate.min.js"></script>
  <script src="app.js"></script>
</head>
<body class="container" ng-app="animateApp" ng-controller="mainController">

  <header class="text-center">
    <h1>Animating Angular Apps<small>ngShow and ngHide</small></h1>

    <!-- use ng-click to toggle true and false -->
    <a class="btn btn-primary" href="#" ng-click="lions = !lions" ng-class="{ active: lions }">Toggle Lions</a>
    <a class="btn btn-success" href="#" ng-click="cranes = !cranes" ng-class="{ active: cranes }">Toggle Cranes</a>
  </header>  
  
  <div class="row">
    <div class="col-xs-6">
    
      <!-- show and hide the lion picture -->
      <div class="jumbotron" ng-show="lions">
        <img src="https://pauljeter.tech/images/lion.jpg" class="img-responsive img-thumbnail">
      </div>
      
    </div>
    <div class="col-xs-6">
    
      <!-- show and hide the crane picture -->
      <div class="jumbotron" ng-show="cranes">
        <img src="https://pauljeter.tech/images/cranes.jpg" class="img-responsive img-thumbnail">
      </div>
      
    </div>
  </div>
  
</body>
</html>
```

Now we have our buttons that will toggle showing and hiding their respective pictures.

With the core stuff out of the way, let’s move onto making our animations work. We just need to define animations in our CSS now and apply them to the classes that ngAnimate gives us (`.ng-hide-add` and `.ng-hide-remove`).

#### CSS Animations
ngAnimate adds the `.ng-hide-add` and `.ng-hide-remove` classes. All we have to do is add animations to those classes.

We’ll borrow some animations from animate.css and then apply those to the right classes.

Here is the full CSS file that will make our app work the way we want. To keep this short, we’ll forego the browser specific prefixes.

```css
/* when hiding the picture */
.ng-hide-add         { animation:0.5s lightSpeedOut ease; }

/* when showing the picture */
.ng-hide-remove      { animation:0.5s flipInX ease; }

/* ANIMATIONS (FROM ANIMATE.CSS) ======================== */
/* flip in */
@keyframes flipInX {
  0% {
    transform: perspective(400px) rotate3d(1, 0, 0, 90deg);
    transition-timing-function: ease-in;
    opacity: 0;
  }

  40% {
    transform: perspective(400px) rotate3d(1, 0, 0, -20deg);
    transform: perspective(400px) rotate3d(1, 0, 0, -20deg);
    transform: perspective(400px) rotate3d(1, 0, 0, -20deg);
    transition-timing-function: ease-in;
    transition-timing-function: ease-in;
  }

  60% {
    transform: perspective(400px) rotate3d(1, 0, 0, 10deg);
    transform: perspective(400px) rotate3d(1, 0, 0, 10deg);
    transform: perspective(400px) rotate3d(1, 0, 0, 10deg);
    opacity: 1;
  }

  80% {
    transform: perspective(400px) rotate3d(1, 0, 0, -5deg);
    transform: perspective(400px) rotate3d(1, 0, 0, -5deg);
    transform: perspective(400px) rotate3d(1, 0, 0, -5deg);
  }

  100% {
    transform: perspective(400px);
    transform: perspective(400px);
    transform: perspective(400px);
  }
}

/* light speed out */
@keyframes lightSpeedOut {
  0% {
    opacity: 1;
  }

  100% {
    transform: translate3d(100%, 0, 0) skewX(30deg);
    transform: translate3d(100%, 0, 0) skewX(30deg);
    opacity: 0;
  }
}

@keyframes lightSpeedOut {
  0% {
    opacity: 1;
  }

  100% {
    transform: translate3d(100%, 0, 0) skewX(30deg);
    transform: translate3d(100%, 0, 0) skewX(30deg);
    transform: translate3d(100%, 0, 0) skewX(30deg);
    opacity: 0;
  }
}
```

Just like that, we have added animations when our pictures are shown and hidden. Go ahead and pull in animate.css into your project and experiment with all the great animations they provide. If you include the file in your project, you won’t have to write out all these animations.


### Conclusion
Just like animating ngView, animating ngShow and ngHide is an easy affair. Just style the classes!