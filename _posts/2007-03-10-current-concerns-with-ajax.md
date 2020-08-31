---
id: 367
title: Current concerns with Ajax
date: 2007-03-10T10:24:44+00:00
author: admin
layout: post
guid: http://www.softwareas.com/current-concerns-with-ajax
permalink: /current-concerns-with-ajax/
dsq_thread_id:
  - "375573255"
categories:
  - SoftwareDev
tags:
  - Accessibility
  - Links
  - Web
  - Web 2.0
---
A reader just mailed me about what I see as concerns with Ajax right now...what's still worryng?

Well, here are a few things off the top of my head...

Accessibility is still a key issue, but more to do with if people bother to Ajaxify at all than if people break accessibility. If developers are required by their companies or regulations to make their web apps accessible, what's the incentive to add Ajax and make it more usable as well? Making a website Ajax-enabled *and* accessible can sometimes be a lot of work. Managers really have to be aware of the benefits of Ajaxifying their apps so they can make a balanced choice.

Documentation for the key open-source frameworks (prototype and dojo) is still very lacking, though it's good for Yahoo! and Mochikit. I really want to use Dojo in a big way and the mailing list support is great, but every time I look for <a href="http://manual.dojotoolkit.org">docs</a>, it's just too discouraging and I revert to Prototype (being the default Rails library of choice). For a long, long, time, Prototype's homepage was completely empty - essentially just a download link. Now there's a little more, and also the Scriptaculous wiki, but still pretty raw.

In this world of mashups, it's ironic that XMLHttpRequest is not at all suited to cross-domain calls. We can sort of work around that with <a href="http://ajaxpatterns.org/Cross-Domain_Proxy">Cross-Domain Proxy</a> or <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a>, but they are both hacks. The first is inefficient as it involves the host server in all calls, the second requires explicit permission and support from the external server. Neither is the ideal, clean, call that XHR was supposed to facilitate. A better model is required. Doug Crockford's JSONRequest will help, but is unlikely to be adopted by MS - in an earnest way - anytime this decade.

Cross-browser programming is still painful. CSS is inconsistent and DOM models vary in subtle ways.

Comet (<a href="http://ajaxpatterns.org/HTTP_Streaming">HTTP Streaming</a>) is becoming really important, but is still out of reach for the typical Ajax programmer. Too resource-intensive, too many issues to overcome, especially in the server.