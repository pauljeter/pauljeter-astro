---
title: 'All About the Built-in AngularJS Filters'
description: 'A guide to the many built-in filters that AngularJS provides out of the box.'
pubDate: '2015-02-19'
heroImage: '/images/angularjs-2.jpg'
---

### Introduction
You may not know this – but AngularJS comes with many handy filters built-in. I see programmers reinventing the wheel and reimplementing functionality that already exists all the time. Sometimes this happens because you need to address a specific use case but more often than not, it’s simply because the programmer wasn’t aware that the functionality was already there.

In this article, I will go over the many filters that AngularJS provides out of the box. Most of these are documented in the Angular Docs but lack real world examples, so I will approach this topic with a plethora of code samples and real world uses.

Let’s jump right into it!

### Applying and Using Filters
Filters, as the name implies, allow you to manipulate and filter the presentation of your views. You can apply Angular filters directly by extending the bindings in your HTML views such as:

#### Basic Filter Syntax
`{{ totalCost | currency }}`

#### Chaining Filters
Filters can also be chained, by adding the pipe ( | ) character between each filter so if we wanted to apply multiple filters to a single expression it would look something like:

`{{ totalCost | currency | filter2 | filter3 }}`

Finally, filters can be extended even further by supporting arguments, for example:

`{{ totalCost | currency:"USD$" }}`

It is common practice to apply filters directly to the binding expressions in the HTML views, but you can also apply filters in your controllers and directives as well.

#### Filters Inside of JavaScript Files
The syntax for applying filters in your JavaScript files will look like this:

`$filter('number')(15, 5)`

This filter is equivalent to `{{ 15 | number:5 }}` and both will render the number 15 as string to five decimal places (i.e. 15.00000) in your view.

It’s ok if you don’t fully grasp what we’re doing so far, we are just going over the syntax here – next we’ll walk through the built in filters and how they can improve the presentation of your apps.

### String Manipulation – Uppercase and Lowercase
AngularJS comes with prebuilt filters for making a string upper or lower-case. The uppercase and lowercase filters will do what their name implies, either convert a string to all uppercase characters, or convert the string to all lowercase characters.

The simplest way to apply this filter to an expression is to add it directly in the view. Please check out the Codepen below to see the Uppercase and Lowercase filters illustrated.

```
// JavaScript
app.controller('limits', function($scope){
  $scope.copy = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
  $scope.yelling = "LOREM ISPUM DOLOR SIT AMET, CONSECTETUR ADIPISCING ELIT, SED DO EIUSMOD TEMPOR INCIDIUNT UT LABORE ET DOLORE MAGNA ALIQUA."
})

// HTML
Uppercase:
{{ copy | uppercase }}

Lowercase:
{{ yelling | lowercase }}
```

### Number Manipulation – Numbers and Currencies
AngularJS also comes with a couple of very useful filters for dealing with numbers and currencies. For numbers, Angular comes with the ability to filter how to number is displayed in regards to the decimal representation and rounding of numbers.

In the Codepen below, we apply a couple of different number filters to display a whole number to four decimal places, we also use the numbers filter to round up a number to the nearest hundredth.

```
// JavaScript
app.controller('numbers', function($scope){
  $scope.defaultNumber = 50;
  $scope.defaultNumberDecimals = 50.458;
})

// HTML
Default Number Filter:
{{ defaultNumber | number }}

Number to Four Decimal Places:
{{ defaultNumber | number:4 }}

Round Number to Two Decimal Places:
{{ defaultNumberDecimals | number:2 }}
```

Part two of number manipulation deals with currencies and AngularJS filters really shine here. By default if we apply the currency filter to a number, it will simply add a $ symbol before the number.

This works really well if you are writing an app that will only deal with dollars, but what if we wanted to localize the app to support a variety of currencies? We can simply expand the currency filter by passing in some parameters to the filter.

For example if we wanted to display the currency in euros, our code would look like {{ totalCost | currency:'€' }}. Additionally, in Angular 1.3+, the currency filter can further be expanded to support rounding up of numbers to as many decimal places as you want – or none at all.

To specify the number of decimal places, you would again just pass another parameter to the currency filter such as {{ totalCost | currency:'$':4 }}, and this would render the number as “$15.0000″ if totalCost was 15.

```
// JavaScript
app.controller('currencies', function($scope){
  $scope.defaultNumber = 59.99;
  $scope.defaultNumberWhole = 59;
})

// HTML
Default Currency Filter:
{{ defaultNumber | currency }}

Currency Filter on Whole Number:
{{ defaultNumberWhole | currency }}

Custom Currency Filter:
{{ defaultNumber | currency:'$COTCHES' }}

Custom Currency Filter with Decimal Point Control (Angular 1.3+):
{{ defaultNumber | currency:'£':0 }}
```

### Date and Time
The Date and Time filters that come with Angular are amazing. The Date and Time filters will take any standard ISO 8601 date/time string and parse it into hundreds of different ways to meet your every need.

Whether you need the full date written as Thursday, October 19, 2014, or just the year, day, month or any combination you can think of such as day first, then the actual day name, followed by the last two digits of the year and concluded by the month in shorthand notation (i.e Nov for November), AngularJS will do it for you.

Parsing and manipulating date/time is often difficult and time consuming but the AngularJS filters make it a breeze. Like I said earlier, there are many different different filters you can apply here, and I could write multiple articles on all the different ways you can apply these filters, but in the interest of time I will direct you to the AngularJS docs that describe all the different parameters you can pass into the date filter and include a CodePen that shows off some of this functionality. Read more about the date filter here.

```
// JavaScript
app.controller('dates', function($scope){
  $scope.dateCommon = "2014-10-19";
  $scope.dateUTC = "2014-10-19T06:46:00+00:00";
})

// HTML
Default Date Filter:
{{ dateCommon | date }}

Full Date Filter:
{{ dateCommon | date:'fullDate' }}

Year Only Filter:
{{ dateCommon | date:'yyyy' }}

Custom Date Filter:
{{ dateUTC | date:"'Year:' yyyy, 'Month:' MMM, 'Day:' EEEE" }}
```

### JSON
The JSON built in filter in Angular converts a json string and prettifies it by including indentation so that the JSON is much easier to read. There really isn’t anything else to say about this filter, it doesn’t allow for any additional parameters to be passed into it, it simply converts an object to easily readable JSON.

Check out the simple CodePen below to see this illustrated.

```
// JavaScript
app.controller('json', function($scope){
  $scope.userInfo = {"name": "Bob", "email": "bob@inbox", "password":"youshallnotpass", "activities": ["jogging", "swimming", "boxing"], "eligibility": true, "hasActiveDevice": false}
})

// HTML
JSON Filter:
{{ userInfo | json }}
```

### LimitTo
The LimitTo filter, as it’s name implies, allows you to limit some string or array to a certain length. For example, applying a limitTo:10 filter to a string that contains 15 characters, would only display the first 10 characters of that string.

LimitTo can also be applied to arrays and can be very powerful and intuitive when used in conjunction with ng-repeat. Combining limitTo and ng-repeat, you could very easily build a pagination system for your app for example.

One common use case where the limitTo filter can come in handy is preview text. Say you’re building the front-page for your blog in AngularJS and want to show a preview of the first 250 characters of each blog post. This can easily be accomplished by the following code {{ previewCopy | limitTo: 250 }}.

Check out the CodePen below to see how we apply the ellipses(…) to the end if the previewCopy is over the character limit.

```
// JavaScript
app.controller('limits', function($scope){
  $scope.copy = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
  
  $scope.list = ['@pauljeter', '@foo', '@bar', '@baz']
})

// HTML
LimitTo Filter Applied to a String:
{{ copy | limitTo:150 }}

LimitTo Filter Applied to an Array:
<ul>
  <li ng-repeat="person in list | limitTo:4"> {{person}} </li>
</ul>
```

### Conclusion
We’ve gone over all of the built-in AngularJS filters. The built-in filters provide a variety of functionality from simple uppercasing of a string to complex manipulation of dates.

We went over the different ways to apply filters, the most common being by applying the filter directly in the binding, but I’ve also shown you how to apply the filter through JavaScript.
