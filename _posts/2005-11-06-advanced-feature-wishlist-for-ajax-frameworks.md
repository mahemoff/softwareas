---
id: 233
title: Advanced Feature Wishlist for Ajax Frameworks
date: 2005-11-06T14:53:41+00:00
author: admin
layout: post
guid: http://www.softwareas.com/advanced-feature-wishlist-for-ajax-frameworks
permalink: /advanced-feature-wishlist-for-ajax-frameworks/
dsq_thread_id:
  - "375572727"
  - "375572727"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Libraries
  - Links
  - Logging
  - Software
  - Web
---
[Looking at](http://www.softwareas.com/8-new-ajax-patterns-diagnosis-and-testing) the best practice/process [patterns](http://ajaxpatterns.org) gave me some ideas for Ajax
frameworks. Here's a few thoughts. I know some frameworks already do some of
these things, though most don't, and none do all of them.

**Logging frameworks** should provide a sensible default, ie log to a div, but allow for more flexiblity on the logging strategy, as in log4j. For example, it would be nice to hook into a local storage solution like [AMASS](http://codinginparadise.org/projects/storage/README.html). I know we can all "spy on users", but a local storage solution lets you amass lots more data, helps solve some privacy issues, and will survive network problems ... could even help restore lots data. I'm obviously thinking more of intranets than public internet apps.

**Mock object frameworks** should, um ,exist. As [I mentioned last week](http://www.softwareas.com/mocks-stubs-dependency-injection-and-xmlhttprequest), there's definitely a good case for a <b>JS mock object library like JMock</b>.

**Web Remoting frameworks** should:

* Provide a **high-level, technology-free, interface, and then implement it in as many ways necessary to support the greatest amount of browsers possible**.  Gloves off - IFrames, Images, Stylesheets ... whatever works.
* **Make access to 3rd-party domains virtually transparent**. e.g. CPaint does this by allowing a proxy option, which points to a proxy running on your server. That aside, calls are same as normal.
* **Support simulation.** Let a caller prep the remoting framework with the 
  response it should provide to a given query. Testing in that way, I could see
  very little reason to ever go back to the real server if you could do this.
* **Support logging.** Rather flabbergasted that I couldn't find a framework that supports logging of remote calls. The new Network Sniffing pattern describes other tricks for logging browser-server traffic, but the JS remoting frameworks ought to take care of it.
* **Support mocking.** In addition to prepping with the response, the caller
  should be able to say "throw an exception if you don't get this query". Note
  that this wouldn't need to be the responsibility of the remoting framework if
  there was a general-purpose mocking framework available.
