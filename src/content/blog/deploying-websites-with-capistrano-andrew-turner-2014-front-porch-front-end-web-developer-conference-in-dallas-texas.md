---
title: "Deploying Websites with Capistrano"
description: ""
pubDate: 2014-10-08
heroImage: '/images/capistrano.jpg'
categories: 
  - "front-porch"
tags: 
  - "conferences-2"
  - "front-porch-2"
  - "frontporch-io"
---

Presented by Andrew Turner at the 2014 Front Porch Front End Web Developer Conference in Dallas, Texas.

[@galenandrew](twitter.com/galenandrew) [lanyrd.com/sdchkf](lanyrd.com/sdchkf)

Aq1 - The conversion optimization agency  
  
Common Deployment Methods

- Server-side Editing
- FTP Upload
- File Syncing
- Live Remote Repositories
- Post-receive Hooks/Webhooks
- Third Party Deployment Services
- Continuous Integration

Deployment Chalenges

- Often a manual process
- High risk of error (easy to break things)
- Potential downtime during upload/sync
- No record of log of deployments
- Typically not well documented or easily distributable
- Difficult to manage for multiple environments
- Updates are difficult to reverse

…especially when a deployment crashes a live site!  
  
Capistrano is a remote server Automation and Deployment tool that provides versioned releases and day rollbacks  
  
How does it work?

- Deployment scripts are stored in your project
- Executed locally from the command line (Ruby Gem)
- Connects directly to your server via SSH
- Checks out code from remote repository to your server
- Performs automated tasks/commands on server (or locally)
- Keeps deployment log and versioned releases
- Provides easy ability to rollback releases

Loca. => Server => Repository

- deploy command is issued on local
- local connects to server via SSH
- server updates project code from repository
- server issues a new release and logs deployment

Installation/Setup

1. Instal Capistrano
    - gem install capistrano
2. Initialize Capistrano in your project
    - cap install

Usage

1. Deploy
    - cap production deploy
2. Rollbak
    - cap production deploy:rollback

Directory Structiure: local/project  
  
\-Capfile  
\-config  
     -deploy  
          -production.rb  
          -staging.rb  
     -deploy.rb  
  
Directory Structure: server  
  
\-current  
\-releases  
     -20141007112233  
     -20140903223344  
     -20140821334455  
\-repo  
\-shared  
\-revisions.log  
  
note: Make sure to point your web host's document root to **current** as it is a symlink to the latex release.  
For example, in the above **current** would be a symlink (alias) to **20141007112233**

* * *

This post is from the Front Porch Conference Series. If you enjoyed it, please check out the others below.

- [Accessibility in Not A Four-letter Word by Kim Lovering](http://www.pauljeter.net/web-development/conferences/front-porch/accessibility-in-not-a-four-letter-word-kim-lovering-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Accessibility in Not A Four-letter Word") 
- [SVG Strikes Back by Matt Baxter](http://www.pauljeter.net/web-development/conferences/front-porch/svg-strikes-back-matt-baxter-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "SVG Strikes Back")
- [How Kids Learn by Chirag Gupta](http://www.pauljeter.net/web-development/conferences/front-porch/how-kids-learn-chirag-gupta-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "How Kids Learn")
- [Intro to WebGL and Three.js by David Lyons](http://www.pauljeter.net/web-development/conferences/front-porch/intro-to-webgl-and-three-js-david-lyons-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Intro to WebGL and Three.js -David Lyons")
- Deploying Websites with Capistrano by Andrew Turner
- [SMACSS Your Sass Up by Mina Markham](http://www.pauljeter.net/web-development/conferences/front-porch/smacss-your-sass-up-mina-markham-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "SMACSS Your Sass Up")
- [Developing Mobile Apps with The Ionic Framework by Justin Noel](http://www.pauljeter.net/web-development/conferences/front-porch/developing-mobile-apps-with-the-ionic-framework-justin-noel-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Developing Mobile Apps with The Ionic Framework -Justin Noel")
- [Context Aware CSS by Matthew Carver](http://www.pauljeter.net/web-development/conferences/front-porch/context-aware-css-matthew-carver-2014-front-porch-front-end-web-developer-conference-in-dallas-texas/ "Context Aware CSS")
