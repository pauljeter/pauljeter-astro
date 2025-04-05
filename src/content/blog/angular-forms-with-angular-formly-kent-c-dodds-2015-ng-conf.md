---
title: "Angular Forms with angular-formly"
description: ""
pubDate: 2015-03-04
categories: 
  - "ng-conf"
tags: 
  - "angularjs"
  - "conferences-2"
  - "frameworks"
  - "javascript"
  - "ng-conf"
  - "web-development"
heroImage: "/images/angular-formly.jpg"
---

Presented by Kent C. Dodds at the 2015 ng-conf in Salt Lake City, Utah.

@kentcdodds

JavaScript powered formly

Forms in HTML can get messy, even with directives. Formly abstracts this away to make it more maintainable.

One dependency needed: api-check

ng-form allows you to nest forms.

To add to your index.html:

```
<script src="node_modules/angular-formly/dist/formly.js"></script>
<script src="node_modules/angular-formly-templates-bootstrap/dist/angular-formly-templates-bootstrap.js"></script>
```

Add to your App:

```
var app = angular.module('app', ['ngAnimate', 'ngMessages', 'ngAria', 'formly', 'formlyBootstrap']);
```

Add your form to the DOM:

```
  <div>
    <h2>New and improved Lightsaber order Form</h2>
    <form name="vm.userForm" ng-submit="vm.onSubmit(vm.user)">
      <formly-form model="vm.user" fields="vm.fields">
        <button type="submit" class="btn btn-default" ng-disabled="vm.userForm.$invalid">Submit</button>
      </formly-form>
    </form>
  </div>
```

Add Form data in your controller:

```
vm.fields = [
    {
      key: 'firstName',
      type: 'input',
      templateOptions: {
        label: 'First Name',
        required: true
      }
    },
    {
      key: 'lastName',
      type: 'input',
      templateOptions: {
        label: 'Last Name',
        required: true
      }
    },
  }
]
```

Outputs the DOM:

![formly1](/formly1-1024x281.png)

Auto-magical Attributes:

```
{
  key: 'postalCode',
  type: 'input',
  templateOptions: {
    label: 'Postal Code',
    type: 'number',
    required: true,
    pattern: '\d{5}'
  }
}
```

ExpessionProperties are used to conditionally change template options:

```
    expressionProperties: {
      'templateOptions.disabled': '!model.email'
    }
```

Custom Templates:

```
  formlyConfig.setType({
    name: 'ngConfInput',
    template: [
      '<div class="{{to.className}}">NG-CONF ROCKS!</div>',
      '<input class="form-control" ng-model="model[options.key]" ng-dblclick="onDoubleClick()" />'
    ].join(' '),
    wrapper: ['bootstrapLabel', 'bootstrapHasError'],
    defaultOptions: {
      templateOptions: {
        label: 'Awesome Input!'
      }
    }
  });
```

 

* * *

This post is from the ng-conf Series. If you enjoyed it, please check out the others below.

-  [Functional Testing with Protractor](http://www.pauljeter.net/web-development/conferences/ng-conf/protractor-testing-in-angularjs-ben-clikinbeard-2015-ngconf/ "Functional Testing with Protractor")
- Angular Forms with angular-formly
- [Advanced angular-animate](http://www.pauljeter.net/web-development/conferences/ng-conf/advanced-angular-animate/ "Advanced angular-animate")
