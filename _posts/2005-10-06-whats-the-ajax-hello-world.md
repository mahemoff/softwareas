---
id: 210
title: 'Chat: The &#8220;Hello World&#8221; of Ajax?'
date: 2005-10-06T21:52:27+00:00
author: admin
layout: post
guid: http://www.softwareas.com/whats-the-ajax-hello-world
permalink: /whats-the-ajax-hello-world/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "383905862"
  - "383905862"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Chat
  - DHTML
  - Examples
  - Hello World
  - Javascript
  - Learning
  - Links
  - Programming
  - Software
  - Tutorials
  - Web
  - Web 2.0
---
[Day Barr](http://daybarr.com/blog/2005/10/06/ajax-chat/):

> Chat is not quite the <a href="http://www2.latech.edu/~acm/HelloWorld.shtml">Hello World</a> of Ajax, but it&#8217;s one of the simplest yet useful things I could do.  I didn&#8217;t learn very much by writing <a href="http://www.daybarr.com/playpen/helloworld/">an Ajax Hello World example</a> and it&#8217;s completely pointless <code>:-)</code>

**As many are learning, an Ajax "Hello World" is pretty easy, provided you've already got a grounding in web/JS programming. So beyond that, what's the quintessential Ajax tutorial app?** Some of the [Ajax](http://www.apress.com/book/bookDisplay.html?bID=10042) [texts](http://manning.com/books/crane) are beginning to pour out, so maybe a pattern will emerge. But, for now, the learning apps of choice seem to be:

* **Chat**. Using [Periodic Refresh](http://ajaxpatterns.org/Periodic_Refresh) to show others' responses (but that's so last Tuesday ... bonus points for [persistent XMLHttpRequest connections](http://www.ajaxian.com/archives/2005/10/synchroedit_yaw.html).
* **Auto-Completion** Using [Suggestions](http://ajaxpatterns.org/Suggestion) to complete the user's query.
* **Live Search** Providing answers while the user types ([Live Search](http://ajaxpatterns.org/Live_Search)), with a visible [Progress Indicator](http://ajaxpatterns.org/Progress_Indicator) during pauses.
* **Slideshow** Another popular category is the image slideshow, often using fancy [visual effects](http://ajaxpatterns.org/One-Second_Spotlight) for transitions.

I'm surprised we haven't seen more people playing with Ajax [wikis](http://jotlive.com) and [RSS aggregators](http://www.backbase.com/demos/RSS/), but I'm sure they're coming.

**BTW, a basic "Hello World" might be easy, but it's also a useful springboard for some important variants.** e.g. Add a long delay in your server and see how the browser script handles a timeout (or simulate a delay with [Julien's GM script](http://blog.monstuff.com/archives/000264.html). e.g. Host the service on another domain and have the server act as a [proxy](http://ajaxpatterns.org/Cross-Domain_Mediator). e.g. Apply a [visual effect](http://ajaxpatterns.org/One-Second_Spotlight) like the famous [Yellow Fade Technique](http://www.37signals.com/svn/archives/000558.php) when the message comes in. These variants aren't just interesting exercises - all are important for real-world Ajax development.
