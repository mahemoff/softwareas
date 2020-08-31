---
id: 177
title: Meta-Search with Ajax
date: 2005-08-13T23:12:32+00:00
author: admin
layout: post
guid: http://www.softwareas.com/meta-search-with-ajax
permalink: /meta-search-with-ajax/
dsq_thread_id:
  - "375572382"
  - "375572382"
categories:
  - SoftwareDev
tags:
  - Aggregator
  - Feeds
  - Links
  - Patterns
  - RSS
  - Search
---
**I just discovered a new feed meta-search: [TalkDigger](http://talkdigger.com/)** (via [Data Mining](http://datamining.typepad.com/data_mining/2005/08/rumour_mull.html)).
It's Ajax search all the way (buzzword overload!).

**The site shows how ideal Ajax is for meta-search. Each time you enter a query, the browser fires off multiple queries - one for each engine it searches.** That means the results all come back in parallel - no bottlenecks.

Back in the day, metacrawler and others were smart enough to start writing out the page straightaway, so users start seeing some results while others are still pending. **The Ajax meta-search improves on the situation by directly morphing the result panels, so the page structure remains fixed even as all the results are populated.** Each panel gets its own [Progress Indicator](http://ajaxpatterns.org/Progress_Indicator).

**This is an example of [Multi-Stage Download](http://ajaxpatterns.org/Multi-Stage_Download) - set up a few empty blocks and populate them with separate queries.** When I initially created the pattern, it was pure speculation, but TalkDigger now makes the third real example I know of. I recently created a [Multi-Stage Download Demo](http://ajaxify.com/run/portal/).

Another nice feature of TalkDigger, which fits well with meta-search, is the use of [Microlinks](http://ajaxpatterns.org/Microlink): **You can click on the results to immediately expand out a summary.**

There's some more features I'm hoping to see:

* The results page definitely needs work - it's nice seeing a brief summary of all results and having them expandable, but it's difficult to get an overall feel. An "Expand All" would help, or showing at least one posting for each search engine.
* The results are broken up by an ad. To me, that's counter-productive as they look like two separate panels. I think most users will mentally filter out the ad anyway and just see the results as broken into two.
* [Sortable columns](http://ajaxpatterns.org/Query-Report Table] - so I could sort by engine name or feed count.
* [Unique URLs](http://ajaxpatterns.org/Unique_URLs) Unique URLs are critical for a search engine. [Unique URL Demo](http://www.ajaxify.com/run/sum/uniqueURL/pollURL/). Jon Udell mentioned the issue recently, regarding MSN Virtual Earth, Google Maps, and others' lack thereof.  [This demo](http://www.ajaxify.com/run/sum/uniqueURL/pollURL/), based on [Mike Stenhouse's ideas](http://www.contentwithstyle.co.uk/Articles/38/fixing-the-back-button-and-enabling-bookmarking-for-ajax-apps) shows it's actually fairly straightforward to emulate standard URLs.