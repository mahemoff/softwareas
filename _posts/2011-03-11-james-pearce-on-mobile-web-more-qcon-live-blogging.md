---
id: 1148
title: 'James Pearce on Mobile Web: More QCon Live Blogging'
date: 2011-03-11T20:37:39+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1148
permalink: /james-pearce-on-mobile-web-more-qcon-live-blogging/
dsq_thread_id:
  - "375981694"
categories:
  - SoftwareDev
tags:
  - Conference
  - html5
  - QCon11
---
Sencha's James Pearce explains why HTML5 rocks mobile apps.

Benefits of the web for mobile apps:

* well understood
* cross-platform
* familiar skills and tools
* decentralised
* easily updated (no store process)
* indexed
* well understood

Mobile is about to explode - where the web escapes and comes with us, to the car and walking around etc.

Same way you had to sit down and listen to the record player instead of having music mobile. "I can't believe you had to sit down to use the web". Use it like a phone, e.g. avoid long forms, make phone numbers clickable, don't include word docs!

The Web is evolving:

* Web of documents is becoming a web of applications
* Declarative HTML becoming programmatic DOM
* Templates becoming APIs on the server-side
* URLs becoming arguments (ie command-line)
* RequestResponse becoming synchronisation

The HTML5 mobile stack looks basically like a native mobile stack

Browsers are much stronger these days, including IE9's effort. But nevertheless, there's still a range of varying support for the browsers.

So can't rely on everything, but some features are there now and diversity is something web developers do have to live with. These tools help:

* http://caniuse.com
* http://modernizr.com
* http://deviceatlas.com

Many mobile frameworks around:
* Sencha (James' company), jQTouch, jQuery Mobile, Sproutcore,
* xui iui zepto embedJS ...

James walks through some of the frameworks. Compared to jQuery mobile, Sencha is more of a pure client-side library - less reliant on a server outputting HTML. Tends to be more script focused than markup. In an MVC way.

Demo: http://sencha.com/x/5e

What W3C calls Thematic Consistency - should get same content on different devices, even if laid out differently. Lots of possibilities - e.g. do you have a special mobile version.

We can have user interface, business logic, and storage on the client; and security and storage on the server.

Whoa - security on two sides means we have a new problem for the web. Storage on both sides. But it's a well-understood problem outside of the web.

