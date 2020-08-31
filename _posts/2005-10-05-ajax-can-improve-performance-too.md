---
id: 208
title: 'Ajax can *Improve* Performance Too'
date: 2005-10-05T22:41:11+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-can-improve-performance-too
permalink: /ajax-can-improve-performance-too/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "399176992"
  - "399176992"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Javascript
  - Kiko
  - Links
  - Patterns
  - Performance
  - Software
  - Web
---
Recent Ajax apps like [Kiko](http://kiko.com) are sluggish according to [Alexander Kirk's "Rise of Slow Ajax Applications](http://alexander.kirk.at/2005/10/04/rise-of-slow-ajax-applications/) (via [AjaxDeveloper](http://www.ajaxdeveloper.org/news/317)):

> Pages get more voluminous because so much code has to be loaded to the browser (which makes the browser slow again) so you could just begin to use the application. This somehow reminds me of all the flash apps. Waiting for hours to load the page and youâ€™ll stick to that page for half a minute.

The initial delay is due to loading of Javascript and data too. Fast startup is certainly a big motivation for Ajax, so it's a problem if that's not happening. 

Alexander gives four tips:

* <i>Keep it bookmarkable. Donâ€™t load everything to one page, let users return to a certain section of your app via their bookmarks.</i>

This is sort of mixing two concepts together. Using [Unique URLs](http://ajaxpatterns.org/Unique_URLs), it's possible for an Ajax app to be bookmarkable, but still the same "page". I think the advice here is to use real page refreshes rather than making an entire website a single Ajax application. I think that's fair for a big corporate website, but for a standalone app like [Kiko](http://kiko.com), it's best seen as a last resort. Saying that, a reasonable use might be in switching between a general login/menu page and the core app itself. Or, in [Writely](http://writely.com), switching between the different tabs - editing, blog it, etc.

* <i>Donâ€™t overuse AJAX.</i> Often simple Javascript without server interaction will do. Try to reduce the server callbacks.

Agree with the tip, though not necessarily the implicit definition that Ajax == server interaction. Rich, standards-based, Javascript is Ajax in my book, and certainly a good way to improve performance.

* <i>Minimize the code to be loaded. When you don't have any other choice, consider code downloading.</i>

Code downloading - or [On-Demand Javascript](http://ajaxpatterns.org/On-Demand_Javascript) - is actually quite easy to do. It involves loading some basic Javascript immediately and continue to load the rest in the background or as needed. You can load the JS by tweaking the head element, or alternatively by pulling it down with XMLHttpRequest and eval'ing it. As an extension of multi-stage code loading, there's also [Multi-Stage Download](http://ajaxpatterns.org/Multi-Stage_Download) - downloading an initial structure upfront and populating it with further calls.

* <i>Speed up your apps with AJAX. Use AJAX for what it was meant for: tune your existing application at points where postbacks need to reload the same page with only little change.</i>

Great point. &lt;rant&gt;Too often, Ajax is blamed for making the web slow, unaccessible, unusable, etc. But what if we stop a minute and ask "What if Ajax could *improve* performance/accessibility/usability? How could that happen?" By attempting to answer these questions as effectively as possible, even if we disagree with the premise, we're better equipped to weigh both sides of the argument.&lt;/rant&gt;

In the case of performance, there are plenty of ways Ajax actually improves the situation. For starters, you don't need to download an entire HTML page every time you talk to the server. More specifically, smart Javascript can do stuff like [caching](http://ajaxpatterns.org/Browser-Side_Cache), [guesstimating](http://ajaxpatterns.org/Guesstimate), and [pre-fetching](http://ajaxpatterns.org/Predictive_Fetch).
