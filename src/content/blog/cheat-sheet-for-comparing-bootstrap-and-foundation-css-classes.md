---
title: 'Cheat Sheet for Comparing Bootstrap and Foundation CSS Classes'
description: 'A comparison of classes between Bootstrap 3 and Foundation 5 by ZURB.'
pubDate: '2015-01-23'
heroImage: '/images/foundation-and-bootstrap.jpg'
---

We've been talking a lot this week about ZURB's Foundation 5. It's a great front-end framework that is a solid alternative to the awesome Bootstrap and deserves at least a look at the features before being dismissed. It does have a few features that Bootstrap doesn't.

This will be a simple article that will help alleviate moving from Bootstrap over to Foundation. We'll be comparing the classes for the main parts of both frameworks. For the most part, both frameworks can build out components of your site for you (grid, buttons, forms, tables), so here's the cheat sheet to see side-by-side classes:

#### Element Class Comparison

<table class="table table-bordered">
  <thead>
    <tr>
      <th class="col-sm-2">Element</th>
      <th class="col-sm-5">Bootstrap</th>
      <th class="col-sm-5">Foundation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="col-sm-2">Alert</td>
      <td class="col-sm-5">
        .alert<br />
        .alert-success<br />
        .alert-danger<br />
        .alert-info
      </td>
      <td class="col-sm-5">
        .alert-box<br />
        .success<br />
        .warning<br />
        .info<br />
        .round<br />
        .radius<br />
        .secondary
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Buttons</td>
      <td class="col-sm-5">
        .btn<br />
        .btn-default<br />
        .btn-primary<br />
        .btn-success<br />
        .btn-info<br />
        .btn-warning<br />
        .btn-danger<br />
        .btn-link<br />
        .btn-lg<br />
        .btn-sm<br />
        .btn-xs<br />
        .btn-block
      </td>
      <td class="col-sm-5">
        .button<br />
        .tiny<br />
        .small<br />
        .large<br />
        .secondary<br />
        .success<br />
        .alert<br />
        .radius<br />
        .round<br />
        .disabled<br />
        .expand
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Lists</td>
      <td class="col-sm-5">
        .list-unstyled<br />
        .list-inline
      </td>
      <td class="col-sm-5">.inline-list (will unstyle it also)</td>
    </tr>
    <tr>
      <td class="col-sm-2">Labels</td>
      <td class="col-sm-5">
        .label<br />
        .label-default<br />
        .label-primary<br />
        .label-success<br />
        .label-info<br />
        .label-warning<br />
        .label-danger
      </td>
      <td class="col-sm-5">
        .label<br />
        .success<br />
        .alert<br />
        .secondary<br />
        .round<br />
        .radius
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Tables</td>
      <td class="col-sm-5">
        .table<br />
        .table-striped<br />
        .table-hover<br />
        .table-bordered<br />
        .table-condensed<br />
        .active<br />
        .success<br />
        .info<br />
        .warning<br />
        .danger
      </td>
      <td class="col-sm-5">
        Tables are automatically formatted with borders, stripes, and headers.
        No extra style classes given.
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Panels</td>
      <td class="col-sm-5">
        .panel<br />
        .panel-default<br />
        .panel-primary<br />
        .panel-success<br />
        .panel-info<br />
        .panel-warning<br />
        .panel-danger
      </td>
      <td class="col-sm-5">
        .panel<br />
        .callout<br />
        .radius<br />
        No other colors provided and no syntax for having a header and body of
        the panel.
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Progress Bars</td>
      <td class="col-sm-5">
        .progress-bar<br />
        .progress-bar-success<br />
        .progress-bar-info<br />
        .progress-bar-warning<br />
        .progress-bar-danger<br />
        .progress-bar-striped<br />
        .active
      </td>
      <td class="col-sm-5">
        .progress<br />
        .small-#<br />
        .large-#<br />
        .secondary<br />
        .success<br />
        .alert<br />
        .radius<br />
        .round
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Text Utilities</td>
      <td class="col-sm-5">
        .text-left<br />
        .text-center<br />
        .text-right<br />
        .text-justify<br />
        .text-nowrap<br />
        .text-lowercase<br />
        .text-uppercase<br />
        .text-capitalize<br />
        .text-muted<br />
        .text-primary<br />
        .text-success<br />
        .text-info<br />
        .text-warning<br />
        .text-danger
      </td>
      <td class="col-sm-5">
        .text-left<br />
        .text-right<br />
        .text-center<br />
        .text-justify<br />
        .small-text-left (also works for medium, large, xlarge)<br />
        .small-only-text-left (also works for medium, large, xlarge)<br />
        .small-text-center (also works for medium, large, xlarge)<br />
        .small-only-text-center (also works for medium, large, xlarge)<br />
        .small-text-right (also works for medium, large, xlarge)<br />
        .small-only-text-right (also works for medium, large, xlarge)<br />
        .small-text-justify (also works for medium, large, xlarge)<br />
        .small-only-text-justify (also works for medium, large, xlarge)
      </td>
    </tr>
    <tr>
      <td class="col-sm-2">Visiblity Classes</td>
      <td class="col-sm-5">
        .visible-*-block<br />
        .visible-*-inline<br />
        .visible-*-inline-block<br />
        .hidden-xs<br />
        .hidden-sm<br />
        .hidden-md<br />
        .hidden-lg
      </td>
      <td class="col-sm-5">
        .show-for-small-only (medium, large, xlarge, xxlarge)<br />
        .show-for-small-up (medium, large, xlarge, xxlarge)<br />
        .hide-for-small-only (medium, large, xlarge, xxlarge)<br />
        .hide-for-small-up (medium, large, xlarge, xxlarge)<br />
        .show-for-landscape<br />
        .show-for-portrait<br />
        .show-for-touch<br />
        .hide-for-touch<br />
        .hidden-for-small-only (medium, large, xlarge, xxlarge)<br />
        .hidden-for-medium-up (large, xlarge, xxlarge)<br />
        .visible-for-small-only (medium, large, xlarge, xxlarge)<br />
        .visible-for-medium-up (large, xlarge, xxlarge)
      </td>
    </tr>
  </tbody>
</table>

### Conclusion

It's interesting to see how each accomplishes certain tasks. Foundation uses universal classes like .secondary, .success, .alert, .radius, and .round while Bootstrap prefixes its classes with the element like .btn-, .alert-, and .panel-.

This could act as a cheat sheet and also a comparison chart for what features are supported. Foundation has a lot of visibility classes compared to Bootstrap while Bootstrap has more flexibility in its table creation.

This should serve as an easy guide to moving between the two front-end frameworks. If you need help finding the correct classes for a certain element, let this little cheat sheet be your guide.

### Want More Foundation?

Here are some more articles to get you going with Foundation:

- [Getting Started with Foundation 5 by ZURB](/blog/getting-started-with-foundation-5-by-zurb)
- [Foundation 5 Features that Bootstrap Doesn't Have](/blog/foundation-5-features-that-bootstrap-doesnt-have)
