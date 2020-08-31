---
id: 196
title: A Few Ajax Gotchas At Jalecode
date: 2005-09-09T19:56:27+00:00
author: admin
layout: post
guid: http://www.softwareas.com/a-few-ajax-gotchas-at-jalecode
permalink: /a-few-ajax-gotchas-at-jalecode/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572535"
  - "375572535"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Gotchas
  - Javascript
  - Links
  - Patterns
  - Software
  - Web
  - XMLHttpRequest
---
[Andrew Sutherland](http://code.jalenack.com/archives/ajax-tips/) offers a few Ajax Gotchas/Tips. I'll add some comments.

* *Escape content with <tt>encodeURIComponent()</tt> which is superior to <tt>escape</tt>.*

* *XMLHttpRequest's <tt>readyState</tt> tells you how far the request has progressed.*
MM: If you're confused about <tt>readyState</tt>'s transition from 0 to 4, you have good reason to be. Read the recent <a href="http://www.davidflanagan.com/blog/2005_08.html#000078">posting and comments</a> on David Flanagan's blog, and you'll learn that 2 and 3 are ambiguous to the point of being unusable. Essentially, you want to wait for either 4 or timeout, and probably ignore everything else.

* *Permission Denied" for <tt>XMLHttpRequest</tt> is usually due to trying to call another domain.*
MM: The standard security policy is that requests can only be sent to the originating server, just like the traditional policy for Java applets. To get to another domain, you can set up a <a href="http://ajaxpatterns.org/Cross-Domain_Mediator">Cross-Domain Mediator</a>. This security issue has become interesting with the growing popularity of Single Page Applications (SPA). What can an HTML page sitting on you hard drive access? All domains or no domains? It would certainly be convenient if it could access the web at large. I don't think it can access any domains on standard browsers, but it's still possible if the user wants it to happen. <a href="http://trimpath.com/project/wiki/SinglePageApplicationAndDevelopmentEnvironment">Here's what Steve Yen (TrimPath) says on this issue:</a> "I'm shooting for now to have explicity user-driven synchronization working, which my experiments lead me to believe is workable."

* MM: Finally, I'll add another gotcha-inspired tip to Andrew's collection:
*Set content type to XML (in the case where you want to treat the response as XML), e.g. in PHP, <tt>header("Content-Type: text/xml");</tt>.*