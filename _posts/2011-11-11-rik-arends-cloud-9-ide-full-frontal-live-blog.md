---
id: 1452
title: 'Rik Arends: Cloud 9 IDE [Full Frontal Live Blog]'
date: 2011-11-11T13:04:00+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1452
permalink: /rik-arends-cloud-9-ide-full-frontal-live-blog/
dsq_thread_id:
  - "468434738"
categories:
  - SoftwareDev
---
Next is Rik Arends, founder/CEO of Cloud 9. (I met Mike and Lieke at Full
Frontal 2 years ago, when they were Ajax.org, and subsequently hosted Rik and
Ruben at Osmosoft, then worked with them on the Cloud 9 Chrome Web Store app
and their Google IO sandbox demo.)

![](http://s1-03.twitpicproxy.com/photos/large/445165979.jpg)

### Why Cloud 9?

A lot of editors treated JS as an afterthought, so we needed a proper
JavaScript editor. We wanted one that wasn't overwhelming, but still did more
than just basic syntax highlighting and formatting, e.g. refactorings. Rik felt
it was important to write a JS IDE in JavaScript; was painful to do something
like this in Eclipse.

Also, IDEs don't need to be ugly or cluttered - they should have a designer feel to
it.

Cloud 9 a year ago was not yet as polished, but the initial version was
received well and there was enough validation to move ahead and bet the company
on it. The team raised venture capital and is setting up in San Francisco.

### Demo

Rik live-demoes a Node "Hello World". Running up the server, checkin to GitHub,
deploy to Heroku.

### Javascript in the Client ...

* APF - high performance UI library
* ACE - source code editor in JS, adapted from Bespin
* Socket.io - real-time socket networking
* jsDAV - file system layer
* Connect - HTTP middleware

### ... And JavaScript in the Server

* Structured exceptions do NOT fit in NodeJS. A single exception for a single
user, if it bubbles up, will blow up the whole server! So can't use exception in
Node the way you use them in JavaScript.
* Beware of globals too, for the same reason. A single global created for a
single user/request will linger. So "use strict" and avoid "closure globals" -
even though they're not truly global, they'll still linger and are best avoided
if possible.
* Avoid state, preferably have none. The thick client makes this real.
* Monitoring Node process with "forever".
* Log everything to reconstruct bugs. You should be able to work out what state
your server was in when the bug occurred.
* Don't blindly trust a library or module right now.

### Where's Cloud 9 Going?

The vision is to have the whole thing online; should never have to revert back
to the local system to deploy.

* Collaboration
* Github Chrome extension - edit GitHub directly
* Multiple buffers - have multiple files open at the same time
* Undeclared variables
* Semantic variables
* Graphical editing inside the (text) editor - e.g. Color picker when you click over
  a color picker
* IE6 support
* Vim mode :D
* IDE Mobile
