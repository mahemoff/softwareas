---
id: 1889
title: 'No, let&#8217;s not use that date format'
date: 2013-02-28T06:19:05+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1889
permalink: /no-lets-not-use-that-date-format/
categories:
  - SoftwareDev
tags:
  - TooSerious
  - XKCD
---
<img src='http://i.imgur.com/qNUzEJ2.png'/>

Doing the rounds is [XKCD's endorsement of the ISO 8601 date format](http://xkcd.com/1179/). Let's avoid that, because as [another XKCD reminds us](http://xkcd.com/927/), you don't just invent new standards in the hope of wiping out the old ones.

![](http://i.imgur.com/RnGMyPN.png) 

I don't know how serious the proposal is, but I'll bite:

* 2013-02-27 is used by no-one; so it will confuse everyone.
* Real people don't use leading zeroes.
* It's still ambiguous. Given dates are already messed up, there's really no reason to assume 2013-02-03 is the logical MM-DD order.

No, the real answer is either include the month name (or abbreviation), or (in a digital context) use the "N days ago" idiom. (Note that "N days ago" does suffer from one major issue, which is it goes stale if caching the content.)

Sure, if the context is filenames or something technical, use this format or just plain old 20130227 (it will sort nicely [as Joel points out](https://twitter.com/CastIrony/status/307014830752149504)) and I often do use this format for backups. But for humans, stick to what they know.