---
title: "Using $stateChangeSuccess to conditionally set $scope variables"
description: ""
pubDate: 2014-10-15
heroImage: '/images/angularjs-2.jpg'
categories: 
  - "angularjs"
tags: 
  - "statechangesuccess"
  - "angularjs"
  - "css3"
  - "javascript"
  - "ui-router"
  - "ui-sref-active"
  - "ui-view"
---

I ran into an interesting issue recently. Using UI-Router, I a ui-vew with a nested ui-view. As the state was changed, I needed the 1st view to slide half way onto the page. Then as the second view was activated, the 1st view would completely slide in, revealing the second view. This sounds like a pretty trivial thing to do using ui-sref-active, however, the nested states presented a problem.

My solution involved using the $stateChangeSuccess event with the ng-class directive to animate the views with classes and CSS3 animations.

```
$scope.userPreviewActive = false;
$scope.userDetailsActive = false;

$rootScope.$on('$stateChangeSuccess', function() {
  if ($state.includes('preview.*')) {
    $scope.previewActive = true;
    $scope.detailsActive = true;
  } else if ($state.includes('preview')) {
    $scope.previewActive = true;
    $scope.detailsActive = false;
  } else {
    $scope.previewActive = false;
    $scope.detailsActive = false;
  }
});
```

Here, I set two flags for the preview pane and the details pane to "false" as the default state of the views. Then, I used the $stateChangeSuccess event to check the state for specific values. I first checked for the preview.\* wildcard for the various details states. I then checked it against the preview state. This allowed me to close these views from either the preview or the details states.

To manipulate the DOM views, I used ng-class to add or remove the two classes from the outer container.

```
<div ng-class="{preview: previewActive, details: detailsActive}"></div>
```

I then used CSS3 animations to slide the view in and out.

```
.container {
  top: 0px;
  right: -110%;
  display: inline-flex;
  height: 100%;
  position: absolute;
  z-index: 1000;
  width: 100%;
  transition: all 500ms cubic-bezier(0.445, 0.05, 0.55, 0.95);
}
.container.preview {
  right: calc(-100% + 350px);
}
.container.preview.details {
  right: -15px;
}
```

Tip: The ui-view directive interferes with the CSS animations if you attempt to use them on the same element. My solution was to wrap the <div> with the ui-view directive in another <div>, and apply the animations to the wrapping container.

If this helped you, please leave a comment or share on your social media of choice.
