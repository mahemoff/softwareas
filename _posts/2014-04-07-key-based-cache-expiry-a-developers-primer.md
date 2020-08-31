---
id: 1945
title: 'Key-based cache expiry: A developer&#8217;s primer'
date: 2014-04-07T11:06:14+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1945
permalink: /key-based-cache-expiry-a-developers-primer/
categories:
  - SoftwareDev
tags:
  - Cache
  - Performance
---
![](http://i.imgur.com/9zmyzax.jpg)

[Key-based cache expiry](http://signalvnoise.com/posts/3113-how-key-based-cache-expiration-works) is a powerful pattern for efficient and reliable caching. I've been using it on for some time now after reading [DHH's original post](http://signalvnoise.com/posts/3113-how-key-based-cache-expiration-works) and it's worked well. This post explains the more conventional approaches to explain how key-based caching arises as a fruitful alternative.

So then, how does caching normally work, and what's so bad about that anyway?

**Clear after some time.** Sure, you can say "this stock price table expires in 5 minutes" and then re-render it every 5 minutes (or longer if no-one immediately requests it). The problem is, you're often making a big compromise on both ends. On the one hand, you'll end up with stale results when the stock price changes during this cache window, e.g. if it changes 2 minutes after you serve it, you're sending wrong data for another 3 minutes. And on the other hand, what if it only changes once a day? Most of the time you're needlessly re-retrieving data, re-calculating and re-rendering it. Wasteful.

**Clear manually.** Seeing the problems of time-based expiry, you could be tempted to just keep the cache up to date manually. So when you're notified of a price change, you explicitly update the value in the cache. This will certainly be more efficient, but the logic gets pretty complex as you scale up. You end up with NxM code complexity as all N bits of code needs to be aware of which M cache items could be affected by changes.

So one technique is easy but inefficient and inaccurate; the other is efficient and accurate, but hard. Let's see if we can find a sweet spot which is easy AND efficient AND accurate.

**Don't clear.** With key-based cache expiry, everything's put there forever and never cleared. How is that possible? Because it takes advantage of the cache's built-in automatic expiry mechanism. We must use a cache, such as Memcached or Redis, which supports some kind of expiry based on least-recently-used (LRU) or similar selection. In that sense, we have reached our application's sweet spot by offloading complexity to the cache framework.

How this works is the keys must reflect a version or timestamp of the object being cached, e.g. a key might be "article-123-201404070123401", generalised as "type-id-timestamp". Normally clients won't request the object by version, so you'll need to do a quick lookup to find the object's latest version or timestamp  [1]. Then you retrieve it from the cache, or write through to the cache if it's not already present. And the important thing is you write to it with infinite expiry.

The technique can be used at many levels - HTTP caching, memcached, persistent databases. I [first asked about it here](http://programmers.stackexchange.com/questions/181888/versioned-resources-to-improve-cacheability) and I've since used it effectively in production on [Player FM's](https://player.fm) website and API. It's certainly how various frameworks handle asset serving (ie compiling CSS with a timestamp and so on), and it's also an official part of Rails 4, and I expect other frameworks in the future. So it's a pattern programmers should be familiar with in an era where performance is held in high esteem, and rightly so.

1.  Looking up timestamp or version is work you don't have to do with manual expiry, so it's again a trade-off that makes this slightly less efficient, but a lot easier. Furthermore, if you arrange things right, you can actually have clients request the latest version/timestamp for all but the original resource (when they are requesting several resources in succession).

Photo Credit: <a href="http://www.flickr.com/photos/97544179@N00/3211076439/">Paolo Margari</a> via <a href="http://compfight.com">Compfight</a> <a href="https://creativecommons.org/licenses/by-nc-nd/2.0/">cc</a>