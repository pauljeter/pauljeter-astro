---
title: "Automate ALL THE FRONT-END THINGS!"
description: ""
pubDate: 2014-11-18
categories: 
  - "javascript-summit"
tags: 
  - "automation"
  - "conferences-2"
  - "front-end"
  - "grunt"
  - "javascript"
  - "node"
  - "npm"
  - "task-runner"
  - "web-development"
heroImage: '/images/javascript-summit.jpg'
---

Presented by Kitt Hodsden at the 2014 JavaScript Summit. [slides](http://ki.tt/jssummit) [@kitt](http://twitter/kitt)

### Guiding principles of Automation:

1. Embrace the Do not repeat yourself (DRY) principle
2. Make changes easy
3. Make finding mistakes easy

**DO WHAT WORKS FOR YOU!**

- implement a design or prototype
- Update the prototype
- make sure it works in all browsers
- do it faster

How often do we have a blank slate, really?

We spend most of our time on 2 and 3.

click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change. click. change.

### browser-sync

###### [http://browsersync.io](http://browsersync.io)

Set up by installing node.js and npm.

$ npm install -g browser-sync

To use browser-sync

`$ browser-sync start --server --files="*.*"`

You can also use a bs.config.js file to setup and start browser-sync

```
$ browser-sync init
[BS] Config file created (bs-config.js)
[BS] To use it, in the same directory run: browser-sync
$
```

 

```
module.exports = {
 files: "css/*.css",
 proxy: {
 host: "localhost",
 port: 8000
 },
 ghostMode: {
 clicks: true,
 links: true,
 forms: true,
 scroll: true
 },
 open: true,
 injectChanges: false,
 notify: true,
};
```

Browser-sync options can be found here. [http://www.browsersync.io/docs/options/](http://www.browsersync.io/docs/options/)

We can use Grunt to automate this process. Grunt is a JavaScript task runner

1. Mature
2. Lots of plugins
3. Strong community
4. Supports gulp & broccoli\*

\*with adaptor, eventually, maybe [http://cowboy.github.io/state-of-grunt-fe-summit-2014-talk/#59](http://cowboy.github.io/state-of-grunt-fe-summit-2014-talk/#59)

### Getting started with Grunt

`$ npm install -g grunt-cli`

`package.json` `Gruntfile.js`

### This is what a package.json file looks like

```
// package.json example

{
 "engines": {
 "node": ">= 0.10.0"
 },
 "devDependencies": {
 "grunt": "~0.4.2",
 "grunt-contrib-jshint": "~0.7.2",
 "grunt-contrib-watch": "~0.5.3",
 }
}
```

With a package.json file, you can install the needed packages easily.

`$ npm install`

Check dependencies into the repo? (I say no)

[http://addyosmani.com/blog/checking-in-front-end-dependencies/](http://addyosmani.com/blog/checking-in-front-end-dependencies/) [http://redotheweb.com/2013/09/12/should-you-commit-dependencies.html](http://redotheweb.com/2013/09/12/should-you-commit-dependencies.html)

### A basic Gruntfile.js file

```
module.exports = function(grunt) {
 // Project configuration.
 grunt.initConfig({
 pkg: grunt.file.readJSON('package.json'),
 uglify: {
 options: {
 banner: '/*! <%= pkg.name %> <%="yyyy-mm-dd") %> */n'
 },
 build: {
 src: 'src/<%= pkg.name %>.js',
 dest: 'build/<%= pkg.name %>.min.js'
 }
 }
 });
 // Load the plugin that provides the "uglify" task.
 grunt.loadNpmTasks('grunt-contrib-uglify');
 // Default task(s).
 grunt.registerTask('default', ['uglify']);
};
```

## browser-sync Grunt example

1. Watch for file changes
2. Refresh the browser on change

### How to add a task to grunt

1. Find grunt plugin\*
2. Install with npm install --save-dev
3. Add the task to our Gruntfile.js file
4. Add the tasks to a command
5. Run the command
6. ...
7. Profit!

\*write if you need to

### Where to find node and grunt packages

[https://www.npmjs.org/](https://www.npmjs.org/)

### Installing the browser-sync grunt package

`$ npm install grunt-browser-sync --save-dev`

```
 browserSync: {
 files: {
 src: [
 'css/*.css',
 'img/*',
 'js/*.js',
 '*.html'
 ]
 },
 options: {
 watchTask: true,
 proxy: {
 host: "localhost",
 port: 8000
 },
 server: false,
 }
 },
```

 

```
 watch: {
 gruntfile: {
 files: '<%= jshint.gruntfile.src %>',
 tasks: ['jshint:gruntfile']
 },
 scss: {
        files: ['scss/*.scss'],
        tasks: ['sass:dev']
      },
      js: {
 // watch for js changes except for script.min.js
        files: ['js/*.js', '!js/script.min.js'], 
        tasks: ['uglify:dev']
      }
 }
```

###  modern.ie

### Make it faster

1. Reduce file sizes
2. Reduce the number of files
3. Reduce content rendering time

#### Images

- npm install grunt-contrib-imagemin --save-dev
- npm install grunt-svgmin --save-dev
- npm install grunt-responsive-images --save-dev
- npm install grunt-grunticon --save-dev

#### Non-images

- npm install grunt-contrib-cssmin --save-dev
- npm install grunt-csscss --save-dev
- npm install grunt-uncss --save-dev
- npm install grunt-contrib-uglify --save-dev

#### Sprites!

- npm install grunt-montage --save-dev

#### Sass / LESS / Stylus

- npm install grunt-contrib-sass --save-dev
- npm install grunt-contrib-compass --save-dev

1. Embrace the Do not repeat yourself (DRY) principle
2. Make changes easy
3. Make finding mistakes easy

**DO WHAT WORKS FOR YOU!**

#### Reduce Content rendering time!

- npm install grunt-devperf --save-dev
- npm install grunt-pagespeed --save-dev
- npm install grunt-criticalcss --save-dev

#### Regression testing

- PhantomCSS
- Wraith
- Diffux
- dpxdt

#### PhantomCSS

- npm install grunt-phantomcss --save-dev

```
phantomcss: {
   desktop: {
     options: {
       screenshots: 'test/visual/desktop/',
       results: 'results/visual/desktop',
       viewportSize: [1024, 768]
}, src: [
       'test/visual/**.js'
] },
   mobile: {
     options: {
       screenshots: 'test/visual/mobile/',
       results: 'results/visual/mobile',
       viewportSize: [320, 480]
}, src: [
       'test/visual/**.js'
] }
}
```

 

```
casper.start('http://localhost:8000/')
.then(function() {
  phantomcss.screenshot('#region-branding', 'region-branding');
}).
then(function now_check_the_screenshots(){
  phantomCSS.compareAll();
});
```

###  Style Guides

- npm install grunt-styleguide --save-dev

### Dev tools

[https://github.com/vladikoff/grunt-devtools](https://github.com/vladikoff/grunt-devtools)
