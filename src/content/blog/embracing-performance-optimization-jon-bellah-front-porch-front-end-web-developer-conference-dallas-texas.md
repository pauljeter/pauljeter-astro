---
title: "Embracing Performance Optimization"
description: ""
pubDate: 2013-10-09
heroImage: '/images/front-porch-2013.jpg'
categories: 
  - "front-porch"
tags: 
  - "front-end"
  - "front-porch-2"
  - "frontporch-io"
  - "javascript"
  - "optimization"
  - "speed"
---

Presented by Jon Bellah at the 2013 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@jonbellah](twitter.com/jonbellah)

[jonbellah.com](http://jonbellah.com)

What is our benchmark? _Sub-second rendering_

Critical Rendering Path

The overview

- minimize requests and round-trip times
- optimize the critical Rendering path

Minimize requests and round-trip times

- Initial connection requires anminimum of 3 RTTs (1 DNS, 1 TCP, 1 HTTP)
- Server can only send ~14kb in the first Round Trip
- Avoid redirects
- Concatenate CSS and JS to reduce requesty
- CSS at the top, JS at the bottom

Optimizing CSS

- Don't load CSS from an asset domain
- avoid duplicate rulesets and otherwise bloated CSS
- Don't use @import in CSS, each occurrence is an HTTP request
- Inline CSS above-the-fold

Leverage Browser Cachiinkg

- Cache rules everything around me
- Cache resources using far-future expires or cache control max age headers
- specify a last-modified or ETag for each cacheable resource
- Load major libraries from Google hosted

Reduce payload

- Gzip compresses based on repeated or readable strings
- minify

Compress and serve scaled images

- sprites
- 220% jpeg at 0 quality
- picturefill / <picture>
- Srcset
- com

Baseline vs Progressive JPEGs

- baseline renders from top-to-bottom
- progressive renders layered scans of increasing quality
- perceived speed vs actual speed

Maximize Parallelization

- Assets domains allow you to fetch more resources in parallel

Prefetch resources

- Lets you tell the browser to start fetching a DNS a fraction of a second before it's needed
- especially helpful for ...

How do we test this stuff?

- Waterfalls
- Real User Monitoring (RUM)
