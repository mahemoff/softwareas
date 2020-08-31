---
id: 235
title: Server-Centric versus Browser-Centric
date: 2005-11-17T01:20:06+00:00
author: admin
layout: post
guid: http://www.softwareas.com/server-centric-versus-browser-centric
permalink: /server-centric-versus-browser-centric/
dsq_thread_id:
  - "375572744"
  - "375572744"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Architecture
  - Frameworks
  - Links
  - Programming
  - Software
  - Web
---
James Strachan: [Is Ajax gonna kill the web frameworks?](http://radio.weblogs.com/0112098/2005/11/16.html#a541):

> So is the web application of the future going to be static HTML & JavaScript, served up by Apache with Ajax interacting with a bunch of XML based web services (maybe using SOAP, maybe just REST etc)? If so, do we really need a web framework thats focussed on HTTP and HTML, or are we just gonna end up developing a bunch of XML based web services and letting Ajax do all the templating, editing and viewing?

While I've kept [an open mind](http://ajaxpatterns.org/Ajax_Frameworks an open mind), **pure separation** is certainly the approach I've been using and advocating. Perhaps server-centric approaches can work okay for some intranet apps where the emphasis is on getting up and running, and where many developers want to focus on server-side concepts like messaging, DB, business logic, etc. But **the bulk of applications are better off as browser-centric**.

**With tools like Dojo, Mochikit, Scriptaculous, Ajax Pages, you can quite happily get the whole UI encapsulated in JS. Amid all the Ruby uptake (and for good reason), JS has also come along nicely over the past twelve months. Not just libraries, but techniques for OO design, testing, etc.**

In addition, as others have pointed out, the approach goes hand-in-hand with SOA: **if you're going to expose a clean [REST API](http://ajaxpatterns.org/RESTful_Service) on your server anyway, it's a no-brainer to proceed with a pure-browser UI.** Testing becomes a lot easier too. Separating model and presentation has always been a difficult problem in software ... when you have a solution as good as this, you have to put up a very strong argument against it.

So why are people still using server-centric frameworks? The biggest force of resistance seems to be the misplaced notion that JS is a hack and we must avoid working with it at all costs. Or maybe it's less ideological than that, and because people just haven't had time to learn it. Fair enough - it's hard enough to keep up with server-side technologies. But a little time learning the basics of JS would certainly ease the pain of web development.