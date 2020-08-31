---
id: 386
title: 'Digg API &#8211; Can&#8217;t Bust the Cache'
date: 2007-06-30T10:22:08+00:00
author: admin
layout: post
guid: http://www.softwareas.com/digg-api-cant-bust-the-cache
permalink: /digg-api-cant-bust-the-cache/
dsq_thread_id:
  - "375573323"
categories:
  - SoftwareDev
tags:
  - API
  - Digg
  - Links
  - Mashup
  - Web2.0
  - XMLHttpRequest
---
<img src="http://picupper.com/2007/06/30/digg.jpg">

It's often a requirement for an Ajax app to "bust the cache", i.e. call a service and ensure its response comes direct and not from a cache. For all the talk of fancy header techniques, the easiest way to do it is by <a href="http://ajaxpatterns.org/XMLHttpRequest_Call">appending an arbitrary parameter</a>, typically a random number and/or a timestamp i.e. call service.com/?random=39583483. I use this pattern not just as an Ajax programmer but also as a user; when I suspect my wiki page or blog is cached, I just add an arbitrary parameter and usually get the most recent result.

With <a href="http://apidoc.digg.com">Digg API</a>, that's impossible. I just tried it and discovered you get an <a href="http://apidoc.digg.com/ListErrors">unrecognised argument error</a> if you pass in a parameter they weren't expecting. This is well-intentioned as it will give early failure advice to callers who mistype or misinterpret parameter names. But unfortunately, it has the major downside of breaking this convention and thus breaking compatibility with a large number of toolkits that exploit this pattern.

I discovered this as I was writing a Google Gadget to show Digg stories and when you fetch content with the Google <tt>API _IG_FetchContent("http://digg.com/....", callbackFunc, { refreshInterval: 60 })</tt> - the refresh option apparently leads to Google tacking on an arbitrary parameter called "cache" (it's impossible to be sure as it's proxied via Google, but the argument to that proxy is the Digg URL with "cache=<random>" on the end). Net effect: I can't update Digg stories any more than once per hour. The only way I could do it would be to write my own proxy and cache. A lot more work than the one-liner _IG_FetchContent call! Yeah, like that's gonna happen.

For the Digg API, perhaps they need to introduce an optional "strict" parameter like a compiler offers to give extra debug info. If it's off, then let anything through.