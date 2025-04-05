---
title: 'Manage Front End Resources with Bower'
description: 'How to efficiently manage and install front-end resources with Bower, a web package manager.'
pubDate: '2013-12-05'
heroImage: '/images/bower.jpg'
---

Bower is a front-end package manager originally developed by Twitter. With experience spanning over a decade in front-end development, working with tools like Angular, React, jQuery, and WordPress, I’ve come to appreciate tools that streamline my workflow. Bower does exactly that for managing web resources.

## Why Use Bower?

There are several compelling reasons to use a front-end package manager like Bower:

- You no longer need to manually download and copy packages into each project.
- You can easily maintain specific versions of resources across multiple projects.
- It simplifies managing multiple dependencies and their updates.

## Quick Example: Using jQuery

### Traditional Method

You’d typically:

- Visit jQuery.com
- Find and download the required version
- Extract and manually copy the files into your project

Alternatively, you might use a CDN, but you'd still need to find and copy the URL each time.

### Bower Method

With Bower, it's as simple as typing:

```bash
bower install jquery
```

This command pulls the resources directly into your project's `bower_components` folder.

## Installing Bower

Bower depends on Node.js and npm. Ensure they are installed first:

```bash
node -v
npm -v
```

Install Bower globally using npm:

```bash
npm install -g bower
```

**Note for Windows Users:**  
Ensure Git is correctly installed, selecting "Run Git from the Windows Command Prompt" during installation.

## Installing Packages with Bower

Use the following syntax to install popular packages:

```bash
bower install jquery
bower install angular
bower install font-awesome
bower install animate.css
```

You can also specify versions:

```bash
bower install jquery#1.8.3
```

## Searching for Packages

To search for packages:

```bash
bower search <package-name>
```

List installed packages:

```bash
bower list
```

Check available packages on the [Bower components site](https://bower.io).

## Configuring Bower for Your Project

To use Bower effectively, you'll need two files:

- `.bowerrc`: Defines where packages are installed
- `bower.json`: Lists project dependencies

### Define Installation Directory

By default, Bower installs packages in `bower_components`. To customize, create `.bowerrc`:

```json
{
  "directory": "libs"
}
```

### Installing Multiple Packages

Create a `bower.json` file listing dependencies:

```json
{
  "name": "sample-app",
  "version": "1.0.0",
  "dependencies": {
    "bootstrap": "latest",
    "font-awesome": "latest",
    "animate.css": "latest",
    "angular": "latest"    
  }
}
```

Install all dependencies with one command:

```bash
bower install
```

## Using Installed Bower Packages

After installation, include your dependencies in your HTML:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <link rel="stylesheet" href="libs/bootstrap/dist/css/bootstrap.min.css">
  <link rel="stylesheet" href="libs/font-awesome/css/font-awesome.min.css">
  <link rel="stylesheet" href="libs/animate.css/animate.min.css">

  <script src="libs/jquery/jquery.min.js"></script>
  <script src="libs/bootstrap/dist/js/bootstrap.min.js"></script>
  <script src="libs/angular/angular.min.js"></script>
</head>
<body>
  <!-- Your content here -->
</body>
</html>
```

## Summary

Bower simplifies managing front-end resources, ensuring efficient and maintainable workflows. While there are now newer solutions like npm or Yarn for front-end package management, Bower remains a reliable tool in certain scenarios.

Explore further in the official [Bower documentation](https://bower.io/docs/) to discover additional features and configuration options.