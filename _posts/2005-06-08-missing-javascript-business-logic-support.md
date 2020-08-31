---
id: 143
title: Missing Javascript Business Logic Support
date: 2005-06-08T09:12:32+00:00
author: admin
layout: post
guid: http://www.softwareas.com/missing-javascript-business-logic-support
permalink: /missing-javascript-business-logic-support/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572316"
  - "375572316"
categories:
  - HumansAndTech
  - Links
---
Marcus Baker recently wrote about [Ajax applications not being responsive enough](http://www.lastcraft.com/blog/index.php?p=19), so the argument goes you should do just about everything in the browser, and mainly use the server-side for periodic persistence. I don't think that's always the right thing to do, but there's definitely going to be more apps developed that way, and there's definitely a performance driver to keep at least some business logic in the browser.

So, after looking at the [various frameworks](http://www.ajaxpatterns.org/AJAXFrameworks), **what's missing among the Javascript offerings is a portable, non-UI, utility library to support business logic**. Such a library wouldn't do any DHTML or DOM manipulation. Instead, it would offer the sort of functionality you'd get from java.util or the STL or various Jakarta classes. A cohesive library of features such as:

* Collections and related algorithms.
* Logging
* Number-crunching algorithms.
* Basic variable manipulation (like [Jakarta Commons Lang](http://jakarta.apache.org/commons/lang/) - simple, oft-repeated code like isWhitespace()).

**Some of this stuff exists already, but it's scattered across the net, with various licenses and inconsistent styles. A worthwhile API would offer this functionality and package it all together, with self-referencing whenever possible** e.g. if it provided a logging framework, all of the packages would take advantage of it. **It would also need to avoid excessive downloading. XMLHttpRequest can actually help here - Alex Russell [recently mentioned](http://smokey.rhs.com/web/blog/poweroftheschwartz.nsf/d6plinks/RSCZ-6CEQAR) that DOJO actually pulls in Javascript on the fly. Also, caching of Javascript files clearly helps a lot. And on intranets, it's usually a non-issue.**

It might also be worthwhile allowing server-side integration via XMLHttpRequest, with sajax-like functionality mapping Javascript functions into server-side calls. For example, a library might work like the dependency injection containers, allowing the caller to configure how particular functions are deployed. You could then switch an implementation over to the server if desired. It's fairly transparent, though with an asynchronous call, the callback function would impose some interference.

I realise there are plenty of problems with Javascript business logic, and it's certainly not always applicable. Those problems include:

* Security - Exposes business logic algorithms and enables them to be changed.
* Complexity - Javascript is more powerful than many people assume, but suffers in comparison to standard language like Java or Ruby, where there is also better library support, development tools, and more established design patterns.
* Footprint - There's the potential to download excessive library code, so careful management is required to avoid that situation.
* Scaleability - While client-side processing can actually out-perform server-side processing when the server is heavily loaded, there's a scaleability problem - you can only run as fast as the client platform.

But having said that, there are places where it makes sense, and we'll be seeing a lot more business logic in the browser. It therefore makes sense to ease the development pain when that happens.
