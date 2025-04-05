---
title: 'Handling Checkboxes and Radio Buttons in Angular Forms'
description: 'A quick tutorial on dealing with checkboxes and radio buttons in Angular forms.'
pubDate: '2014-09-15'
heroImage: '/images/angularjs-2.jpg'
---

AngularJS makes dealing with forms extremely easy. When it comes to two-way data-binding to the way it helps us handle form validation, Angular really helps us process forms.

We’ve written in the past on the great features of Angular in forms and how to process forms. Today will be a quick tutorial on dealing with checkboxes and radio buttons in Angular forms.

There are many different use cases for checkboxes and many different ways we can process them. We’ll take a look at the ways to bind checkboxes and radio buttons to data variables and the ways we can tweak them.

### Setting Up Our Angular Form
For this tutorial, we will need 2 files. index.html and app.js. app.js will hold all of our Angular code (it won’t be much) and index.html will be where all the action happens. Let’s create our AngularJS file first.

```javascript
// app.js

var formApp = angular.module('formApp', [])

    .controller('formController', function($scope) {
  
        // we will store our form data in this object
        $scope.formData = {};
        
    });

```

All we do in this file is set up our Angular application. We will also create a controller and an object to hold all of our form data.

Now let’s look at our index.html file where we will create our form and do all of our data binding. We’ll be using Bootstrap to help speed up our stylings.

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>

    <!-- CSS -->
    <!-- load up bootstrap and add some spacing -->
    <link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.1.1/css/bootstrap.min.css">
    <style>
        body         { padding-top:50px; }
        form         { margin-bottom:50px; }
    </style>

    <!-- JS -->
    <!-- load up angular and our custom script -->
    <script src="http://code.angularjs.org/1.2.13/angular.js"></script>
    <script src="app.js"></script>
</head>

<!-- apply our angular app and controller -->
<body ng-app="formApp" ng-controller="formController">
<div class="col-xs-12 col-sm-10 col-sm-offset-1">

    <h2>Angular Checkboxes and Radio Buttons</h2>

    <form>
    
        <!-- NAME INPUT -->
        <div class="form-group">
            <label>Name</label>
            <input type="text" class="form-control" name="name" ng-model="formData.name">
        </div>
        
        <!-- =============================================== -->
        <!-- ALL OUR CHECKBOXES AND RADIO BOXES WILL GO HERE -->
        <!-- =============================================== -->
        
        <!-- SUBMIT BUTTON (DOESNT DO ANYTHING) -->
        <button type="submit" class="btn btn-danger btn-lg">Send Away!</button>
        
    </form>
    
    <!-- SHOW OFF OUR FORMDATA OBJECT -->
    <h2>Sample Form Object</h2>
    <pre>
        {{ formData }}
    </pre>
    
</div>
</body>
</html>
```

With this setup, we will now have our form ready to go with a name input. If all went according to plan, if you type into that name input, you should see your data populate in the <pre> tag below.

### Checkboxes
Checkboxes are extremely common in any form. Let’s look at how Angular binds their data using ngModel. When there are many checkboxes, sometimes it can be confusing to now how to handle that data when binding it to an object.

Inside of the formData object we created, we will create another object. Let’s call this one favoriteColors and ask our user what their favorite colors are.

```html
    <!-- MULTIPLE CHECKBOXES -->
    <label>Favorite Colors</label>
    <div class="form-group">
        <label class="checkbox-inline">
            <input type="checkbox" name="favoriteColors" ng-model="formData.favoriteColors.red"> Red
        </label>
        <label class="checkbox-inline">
            <input type="checkbox" name="favoriteColors" ng-model="formData.favoriteColors.blue"> Blue
        </label>
        <label class="checkbox-inline">
            <input type="checkbox" name="favoriteColors" ng-model="formData.favoriteColors.green"> Green
        </label>
    </div>
```

When a user clicks on one of the checkboxes, they will see that the formData object immediately changes. We are housing the values for our checkboxes in the formData.favoriteColors object and this is how we will pass data of our checkboxes to our server.

### Processing a Change on Checkbox Click
Sometimes you will need to process something when somebody clicks a checkbox. This could be something like doing a calculation, changing some variables, or whatever data-binding things you need to do. To do this, you would create a function inside of `app.js` using `$scope.yourFunction = function() {}`.

There are many different uses for this in forms and Angular provides a very easy way to call custom functions using `ng-click`.

### Custom Values for Checkboxes
By default, bound checkboxes will return `true` or `false`. Sometimes we want to return different values. Angular provides a great way to do this using `ng-true-value` and `ng-false-value`.

Let's add another set of checkboxes, but this time, instead of `true` or `false`, we will use custom values.

```html

    <!-- CUSTOM VALUE CHECKBOXES -->
    <label>Personal Question</label>
    <div class="checkbox">
        <label>
            <input type="checkbox" name="awesome" ng-model="formData.awesome" ng-true-value="ofCourse" ng-false-value="iWish">
            Are you awesome?
        </label>
    </div>
```

With this addition, we now have an `awesome` variable in our formData object. If this is set to true, the value will be `ofCourse` and if set to false, the value will be `iWish`.

### Checkbox Usage
Per the official docs, here are the different things you are able to do with checkboxes:

```html
    <input type="checkbox"
       ng-model="string"
       value="string"
       [name="string"]
       [ng-change="string"]
       ng-true-value="string"
       ng-false-value="string">
```

  For more information on the things you can do with checkboxes, read the Angular input[checkbox] docs.

### Radio Buttons
Radio buttons are a little bit easier than checkboxes since we don’t have to store multiple values. A radio button will just be one value since you can only select one thing. Let’s add in radio boxes and see how they are data-bound.

```html
    <input type="radio"
       ng-model="string"
       value="string"
       [name="string"]
       [ng-change="string"]
       ng-value="string">
```

For more information on the things you can do with checkboxes, read the Angular input[checkbox] docs.

### Radio Buttons
Radio buttons are a little bit easier than checkboxes since we don’t have to store multiple values. A radio button will just be one value since you can only select one thing. Let’s add in radio boxes and see how they are data-bound.

```html
    <!-- RADIO BUTTONS -->
    <label>Chicken or the Egg?</label>
    <div class="form-group">
        <div class="radio">
            <label>
                <input type="radio" name="chickenEgg" value="chicken" ng-model="formData.chickenEgg">
                Chicken
            </label>
        </div>
        <div class="radio">
            <label>
                <input type="radio" name="chickenEgg" value="egg" ng-model="formData.chickenEgg">
                Egg
            </label>
        </div>
    </div>
```

Just like that, our radio buttons are now bound to our formData object.

### Radio Button Usage
Per the official docs, here are the different things you are able to do with radio buttons:

```html
    <input type="radio"
       ng-model="string"
       value="string"
       [name="string"]
       [ng-change="string"]
       ng-value="string">
```

For more information on the things you can do with radio buttons, read the Angular input[radio] docs.

### Conclusion
As you can see, binding checkboxes and radio buttons using Angular is a fairly easy process. There is also a lot of flexibility when you want to change parts of your application or create specialized checkbox or radio buttons.