---
title: "Functional Testing with Protractor"
description: ""
pubDate: 2015-03-04
categories: 
  - "ng-conf"
tags: 
  - "angularjs"
  - "frameworks"
  - "front-end"
  - "jasmine"
  - "javascript"
  - "js"
  - "protractor"
  - "testing"
  - "web-development"
heroImage: "/images/protractor.jpg"
---

Presented by Ben Clinkinbeard at the 2015 ng-conf in Salt Lake City, Utah.

[@bclinkinbeard](https://twitter.com/bclinkinbeard)

Live coding files at bit.ly/ng-ptor

Slides located at bit.ly/ng-ptor-slides

**How It Works**

- Your tests call Protractor APIs
- Protractor extends/calls selenium-webdriver (running in Node)
- selenium-webdriver calls a (local or remote) Selenium server
- Selenium server calls a browser driver
- Browser driver uses your app as a user would

Terminology is a mess.

- selenium-webdriver
- WebdriverIO
- wd

**Protractor**

- Best JS Selenium API available
- Literally extends selenium-webdriver
- Adds Angular-specific APIs
- Understands Angular's run loop
- Provides helpers
- Your tests call Protractor APIs
- Protractor extends/calls selenium-webdriver (running in Node)
- selenium-webdriver calls a (local or remote) Selenium server
- Selenium server calls a browser driver
- Browser driver uses your app as a user would

```
element(by.css('button.myclass')).click();
```

- POST /session/:sessionId/execute\_async
- POST /session/:sessionId/element
- POST /session/:sessionId/element/:id/click

**WebDriver Control Flow**

- Each command add a promise to the stack/chain
- Protractor adapts Jasmine to wait for empty stack
- Other test libs can be used

```
browser.get('.signin');

var username = element(by.model('username'));
username.clear();
username.sendKeys
```

 **Protractor API**

- browser
- element()
- element.all()
- by
- driver

**API - Locators**

- click()
- getText()
- sendKeys()
- clear()
- isPresent()
- ...

**Page Objects**

- Useful Essential for maintainable test code
- Softens the blow of app changes
- page.submitButton YES
- page.submitButton.click() YES
- page.clickSubmitButton() NO

**Advanced Config**

- Reading CLI params
- Extracting browser definitions
- Extracting provider configs
- Testing multiple browsers

**Advanced Locators**

```
element.all(by.binding('item.name')).first();

element(by.css('.list')).all(by.tageName('li')).get(2);
```

 **Test suites**

- Divide tests into subsets
- Good for organization
- Good for dev speed

**Screenshots**

- browser.takeScreenshot().then(callback)
- Can run in afterEach
- Only on failure for debugging
- On all tests for visual regression testing

Providers

- Sauce Labs
- BrowserStack
- Others…

Why Providers?

- Managed Selenium infrastructure
- Hundreds of platforms
- Dashboards
- CI Integration

* * *

This post is from the ng-conf Series. If you enjoyed it, please check out the others below.

-  Functional Testing with Protractor
- [Angular Forms with angular-formly](http://www.pauljeter.net/web-development/conferences/ng-conf/angular-forms-with-angular-formly-kent-c-dodds-2015-ng-conf/ "Angular Forms with angular-formly")
- [Advanced angular-animate](http://www.pauljeter.net/web-development/conferences/ng-conf/advanced-angular-animate/ "Advanced angular-animate")
