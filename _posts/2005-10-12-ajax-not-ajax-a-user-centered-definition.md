---
id: 216
title: 'Ajax, not &#8220;AJAX&#8221;: A User-Centered Definition'
date: 2005-10-12T23:33:09+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-not-ajax-a-user-centered-definition
permalink: /ajax-not-ajax-a-user-centered-definition/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572626"
  - "375572626"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Javascript
  - Links
  - RichClient
  - Web 2.0
  - XMLHttpRequest
---
Many equate Ajax to "Is it using XMLHttpRequest?", which I think is taking the acronym too literally. There's a reason why I've learned to say ["Ajax" rather than "AJAX"](http://en.wikipedia.org/wiki/Talk:Ajax_%28programming%29/Archive_PageMove): **the term is user-centric, not techno-centric, and best defined in terms of what it gives users rather than how you deliver it. And what it gives users is a rich, continuous, experience to rival the desktop, with standards-based technologies.**

Jesse James-Garret, who [coined the term](http://www.adaptivepath.com/publications/essays/archives/000385.php), doesn't define Ajax in terms of specific technologies. Here's what he said in [the recent Ajaxian.com podcast interview](http://www.ajaxian.com/archives/2005/09/audible_ajax_ep.html):
"In my opinion, Ajax refers simply to using browser-native technologies, open standard technologies, in ways that depart from the traditional interaction model of the web - the kind of call-and-response interaction model where every user action is tied to some kind of server communication, and while that server communication is going on, no user actions can take place. Any time you're decoupling the flow of user interaction with the application from the flow of server communication,  and you're doing that with browser-native standard technologies, I think that's Ajax."

If you can pull off a rich browser client using HTML 1.0, you got Ajax! In reality, you'll end up using a mix of technologies suggested by the acronym ("Asynchronous Javascript and XML") and some other things too ("DOM/DHTML/CSS"), but not necessarily all of those things. Having peeked under the covers of various high-profile Ajax sites, it's clear that many are using custom-format messages, rather than XML for transfer. **Similarly, XMLHttpRequest is not the only valid means of transfer.** Google Maps uses IFrames, I've come across various enterprise systems that do the same, and I expect other Ajax apps do it too (and still on the lookout for examples BTW).<!--38fd8f947f92017b62252df4f108d6a7-->