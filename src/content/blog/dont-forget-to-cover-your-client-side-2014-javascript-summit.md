---
title: "Don't forget to cover your client side!"
description: ""
heroImage: '/images/javascript-summit.jpg'
pubDate: 2014-11-18
categories: 
  - "javascript-summit"
tags: 
  - "conferences-2"
  - "javascript"
  - "javascript-summit"
  - "js"
  - "jssummit"
  - "qunit"
  - "tdd"
  - "testing"
---

Presented by Jonathan Creamer at the 2014 JavaScript Summit.  
[@jcreamer898](twitter.com/jcreamer898)  
[slides](http://presentboldly.com/jcreamer898/dont-forget-to-cover-your-client-side/)

> ### Legacy code is code without tests.
> 
> \-Michael Feathers, _Working Effectively with Legacy Code_

## What is a "unit test"

unit - An individual thing or person regarded as a single and complete but which can also form an individual component of a larger or more complex whole.

test - A procedure intended to establish the quality performance, or reliability of something, especially before it is taken into widespread use.

### A unit test therefore is…

A method by which we determine if a given “unit” of code behaves as expected by asserting it’s results given certain parameters and conditions.

Prevent Bugs

- helps release LESS buggy code
- you have tests to prove stuff works
- Bug record keeping
- Now vs later

If you don't do it, someone else will.

![](/ThwZ3Bn.png)

### Code Design

- Designing the API
- Forces you to consider different edge cases
- Makes adding new features without breaking things easier
- Creates living breathing documentation

>  If code is tested, then it is typically understandable and maintainable because it has been written to be tested
> 
> \-Cody Lindley

### Maintainable features === testable features

- The results of maintainable code are often the same as the results of testable code
- Small functions
- Easy to read
- Documented
- De-coupled
- Re-usable

### Types of Testing

###### Unit, BDD, TDD, Integration, etc etc.

- There are many different types
- Unit tests
- Test First
- TDD - Test Driven Development
- BDD - Behavior Driven Development
- Integration
- Regression

### TDD

- The solution needs to be the simplest solution
- Be sure to isolate to a unit
- Don’t write “future code” write “make it pass” code
- Improve the design of the API
- Makes refactoring easier
- Helps reduce coupling

### Client Side Testing

- JavaScript applications are much much larger
- Compile at run time
- Test offline
- Can test outside of the browser

### Excuses, excuses...

- Client side unit testing presents different challenges than server side testing.
- That whole DOM thing
- It’s tempting to just “reload develop”
- “More code”
- “More work”

## Getting Started

- Abstract the DOM
- Use a framework/tool like angular, backbone, or knockout
- Pick a test library
- Pick a mock library
- TDD a bug or three

### QUnit

- QUnit is a simple testing library for JavaScript
- Written by the jQuery team
- Simple setup and assertions
- Low barrier to entry

### QUnit First Steps

###### Easy setup

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>QUnit Example</title>
  <link rel="stylesheet" href="//code.jquery.com/qunit/qunit-1.14.0.css">
</head>
<body>
  <div id="qunit"></div>
  <div id="qunit-fixture"></div>
  <script src="//code.jquery.com/qunit/qunit-1.14.0.js"></script>
  <script src="yourCode.js"></script>
  <script src="tests.js"></script>
</body>
</html>
```

###  module

```
module('test stuff', {
    setup: function() {
        // test
    },
    teardown: function() {
        // after
    }
});
```

### Assertions

###### equal(actual, expected, \[message\]);

```
function add(x, y) {
    return x + y;
}
test("equal", function() {
    var sum = 4;
    equal(add(2, 2), sum, "these two numbers are equal");
});
test("loose equal", function() {
    equal(2, "2");
});
```

```
test('equality', function() {
    var obj = { foo: 'bar' };
    equal(obj, { foo: 'bar'});
});
```

###### deepEqual(actual, expected, \[message\]);

```
test('deep equality', function() {
    var obj = { foo: 'bar' };
    deepEqual(obj, { foo: 'bar'});
});
```

###### ok(actual, \[message\]);

```
function isNumber(val) {
    return !isNaN(Number(val));
}

test('isNumber', function() {
    var num = 7;
    ok(isNumber(num));
});
```

###### throws(block, expected, \[message\]);

```
var doIt = function(x) {
    if (!x) {
        throw "hey now!";
    }
};

test('throws', function() {
    throws(function() {
        doIt();
    }, "hey now!");
});
```

######  propEqual(actual, expected, \[message\]);

```
function Foo(bar) {
    this.bar = bar;
}

test('propEqual', function() {
    var foo = new Foo(1);
    propEqual(foo, { bar: 1 });
});
```

###  Assertions

- Every assertion has a “not”
- They aren’t used very often though
- `notOk`, `notEqual`, etc…

### Async

```
asyncTest('setTimeout', function() {
    function fooAsync() {
        var dfd = $.Deferred();
        
        setTimeout(function() {
            dfd.resolve([1,2,3]);
        }, 0);
        
        return dfd.promise();
    }
    
    fooAsync().done(function(arr) {
        equal(arr.length, 3);
        start();
    });
});
```

## Unit tests 100% pass, code still crashes!

### Mocking with Sinon.js

- In every unit test, there should be one unit under test
- Unit tests need to be as isolated as possible
- Mocking helps remove dependencies
- Spy
- Stub
- Mock
- Other stuff too…

### Spy

- A function that either wraps an existing function or is anonymous and records arguments, return value, exceptions

```
test('spy', function(){ 
    var spy = sinon.spy();

    var $div = $("<div />").on("click", spy);

    $div.trigger("click");

    ok(spy.calledOnce);
});
```

###  Stub

- Functions (spies) with pre-programmed behavior.

```
test('stub', function(){ 
    function ajax(options) {
        return $.ajax(options)
    }

    sinon.stub(jQuery, "ajax").returns({
        done: $.noop
    });

    ajax({ url: "/foo" });

    ok(jQuery.ajax.calledOnce);

    jQuery.ajax.restore();
});
```

###  Stub

```
test('stub', function(){ 
    var callback = sinon.stub();

    callback.onCall(0).returns(1);
    callback.onCall(1).returns(2);
    callback.returns(3);

    equal(callback(), 1);
    equal(callback(), 2);
    equal(callback(), 3);

});
```

### Mock

- Combo of a spy and stub with preprogrammed expectations

```
test('mock', function(){ 
    var listeners = {
        click: function(){}
    };
    var mock = sinon.mock(listeners);
    mock.expects("click").once();

    var $div = $("<div />").on("click", listeners.click);

    $div.trigger("click");

    ok(mock.verify());
});
```

###  Test Coverage

- Analyses which parts are tested
- Blanket, JSCover, Istanbul…
- Set a metric
- May or not be accurate, but it helps!

###  Plato

- Measure the complexity of your code
- Checks for errors
- Keeps track of code over time
- Provides a maintainability score
- [http://jscomplexity.org/complexity](http://jscomplexity.org/complexity)

## Automate automate automate

### Grunt FTW

- Grunt is a node.js based task runner
- Huge community support
- Config file based setup
- Can automate many things
- Tests, concat, uglify, etc

- Easy setup
- Install node
- Setup a `package.json`
- Use npm to install grunt

```
npm install -g grunt-cli
cd project-directory
npm init
npm install grunt --save-dev
npm install grunt-contrib-qunit --save-dev
```

### Live Demo

Check it out at [http://jcreamer898.github.io/cover-your-client-side/](http://jcreamer898.github.io/cover-your-client-side/)
