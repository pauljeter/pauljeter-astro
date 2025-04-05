---
title: 'Understanding the Bootstrap 3 Grid System'
description: 'A practical guide to understanding and effectively using the Bootstrap 3 grid system for responsive web design.'
pubDate: '2014-08-30'
heroImage: '/images/bootstrap-3.jpg'
---

Bootstrap 3 has introduced significant changes to its grid system, adopting a mobile-first approach. With my experience in front-end development over two decades, working extensively with responsive frameworks like Bootstrap, here’s my guide to understanding and utilizing this powerful tool.

## What's New in Bootstrap 3?

Bootstrap 2 primarily focused on desktop layouts, with responsive elements stacking only on mobile. Bootstrap 3, however, starts from mobile-first, scaling upwards to larger devices.

### Bootstrap 2

Previously, grids stacked below 767px, limiting flexibility since you could only define a single grid structure for desktop-sized screens.

### Bootstrap 3

Bootstrap 3 lets you define distinct grids at multiple breakpoints, scaling upwards from mobile. Here's how this works practically:

- 1 column for extra small devices (default)
- 2 columns for small and medium devices
- 4 columns for large devices

```html
<div class="row">
  <div class="col-sm-6 col-lg-3">
    This is part of our grid.
  </div>
  <div class="col-sm-6 col-lg-3">
    This is part of our grid.
  </div>
  <div class="col-sm-6 col-lg-3">
    This is part of our grid.
  </div>	
  <div class="col-sm-6 col-lg-3">
    This is part of our grid.
  </div>	
</div>
```

You only define grid sizes for the smallest breakpoint you want to customize. Larger devices inherit this grid definition unless specifically overridden.

## Bootstrap Grid Sizes

Bootstrap 3 provides four breakpoints to build responsive layouts:

| Class Prefix | Device Size   | Description                 |
| ------------ | ------------- | --------------------------- |
| `.col-xs-`   | < 768px       | Extra Small Devices (Phones)|
| `.col-sm-`   | ≥ 768px       | Small Devices (Tablets)     |
| `.col-md-`   | ≥ 992px       | Medium Devices (Desktops)   |
| `.col-lg-`   | ≥ 1200px      | Large Devices (Desktops)    |

For detailed sizing and columns, check the [Bootstrap Documentation](https://getbootstrap.com/docs/3.4/css/#grid).

## Responsive Utilities

Bootstrap 3 includes helpful utilities for hiding or displaying elements based on device size:

- `.visible-xs`, `.visible-sm`, `.visible-md`, `.visible-lg`
- `.hidden-xs`, `.hidden-sm`, `.hidden-md`, `.hidden-lg`

These are especially useful in creating dynamic layouts that adjust to different screen sizes.

## Practical Examples

### Simple Grid Example: Desktop vs Mobile

Suppose you want:

- 1 column on XS and SM devices
- 2 columns on MD devices
- 4 columns on LG devices

Here's how you'd set it up:

```html
<div class="row">
  <div class="col-md-6 col-lg-3">
    <div class="visible-lg text-success">Large Devices!</div>
    <div class="visible-md text-warning">Medium Devices!</div>
    <div class="visible-xs visible-sm text-danger">Extra Small and Small Devices</div>
  </div>
  <!-- Repeat similar columns as needed -->
</div>
```

### Intermediate: Sidebar Visibility on Large Devices

For a layout that changes from one column on mobile to two columns on medium devices and adds a third sidebar column on large devices:

```html
<div class="row">
  <div class="col-sm-9 col-lg-6 text-danger">
    I am the main content.
  </div>
  <div class="col-sm-3 text-warning">
    I am the main sidebar.
  </div>
  <div class="col-lg-3 visible-lg text-success">
    I am the secondary sidebar shown only on large devices.
  </div>
</div>
```

### Advanced: Different Grid for Each Device Size

Here’s a scenario where each device size has a unique layout:

- XS devices: 2 columns
- SM devices: 3 columns
- MD devices: 4 columns
- LG devices: 6 columns (one column visible only on large screens)

```html
<div class="row">
  <div class="col-xs-6 col-sm-4 col-md-3 col-lg-2">I'm content!</div>
  <div class="col-xs-6 col-sm-4 col-md-3 col-lg-2">I'm content!</div>
  <div class="col-xs-6 col-sm-4 col-md-3 col-lg-2">I'm content!</div>
  <div class="col-xs-6 col-sm-4 col-md-3 col-lg-2">I'm content!</div>
  <div class="col-xs-6 col-sm-4 col-md-3 col-lg-2">I'm content!</div>
  <div class="col-xs-6 col-sm-4 col-md-3 col-lg-2 visible-lg">I'm content only visible on large devices!</div>
</div>
```

## Conclusion

Bootstrap 3's grid system is incredibly flexible, making it straightforward to create dynamic and responsive layouts tailored specifically to each device. Whether building simple mobile-friendly sites or complex layouts with conditional elements, Bootstrap 3 provides all the tools necessary for modern responsive design.
