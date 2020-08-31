---
id: 1906
title: About WebWait and Caching
date: 2013-03-15T13:50:16+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1906
permalink: /about-webwait-and-caching/
categories:
  - General
tags:
  - Caching
  - HTTP
  - WebWait
---
I received today a question often asked about [WebWait](http://webwait.com), so I'll answer it here for reference.

WebWait User asks:

_I have been using webwait for a while and have a quick question for you. When running multiple  calls on the same website, is each call downloading the entire page again, or is the information being loaded from the browser cache?_

My answer:

_It will do whatever the browser would do if the page was loaded normally, so that would usually mean the 2nd-Nth time it will download from the cache. To counter-act that, you can simply disable your browser cache while performing your tests. Or if you do *want* to test cache performance, just open your site once (either in the browser or WebWait) and then start the WebWait tests, obviously keeping the cache enabled throughout._