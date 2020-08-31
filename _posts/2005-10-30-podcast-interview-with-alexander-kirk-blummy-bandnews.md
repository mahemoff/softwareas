---
id: 226
title: Podcast Interview with Alexander Kirk (Blummy, Bandnews)
date: 2005-10-30T14:30:53+00:00
author: admin
layout: post
guid: http://www.softwareas.com/podcast-interview-with-alexander-kirk-blummy-bandnews
permalink: /podcast-interview-with-alexander-kirk-blummy-bandnews/
enclosure:
  - |
    http://softwareas.com/podcast/SASD_AlexKirk_AjaxBlummy.mp3
    22760851
    audio/mpeg
  - |
    http://www.softwareas.com/podcast/SASD_AlexKirk_AjaxBlummy.mp3
    22760851
    audio/mpeg
  - |
    http://softwareas.com/podcast/SASD_AlexKirk_AjaxBlummy.mp3
    22760851
    audio/mpeg
  - |
    http://www.softwareas.com/podcast/SASD_AlexKirk_AjaxBlummy.mp3
    22760851
    audio/mpeg
dsq_thread_id:
  - "375572691"
  - "375572691"
categories:
  - Links
  - Podcast
  - SoftwareDev
tags:
  - AjaxPatterns
  - BandNews
  - Blummy
  - Bookmarklet
  - Links
  - Podcast
  - Software
  - Web
  - Web2.0
---
**This 47-minute podcast is a discussion with [Alexander Kirk](http://alexander.kirk.at/)**, creator of the recently released [Blummy](http://blummy.com) (which I [mentioned last week](http://www.softwareas.com/blummy-the-mother-of-all-bookmarklets)) and also [Bandnews](http://bandnews.org).

<a href="http://www.softwareas.com/podcast/SASD_AlexKirk_AjaxBlummy.mp3"
title="Click to download the Podcast and play it on your computer."
style="text-decoration: none;"><img src="/images/aquapodcastfileicon.gif"
border="0" alt="Click to download the Podcast. You can also subscribe to the
feed if you want future podcasts automatically downloaded - check out the
podcast FAQ at http://podca.st." border="0"/></a>

A few things we discussed:

* **The design behind Blummy.** (Interestingly, I was incorrect to guess it uses XHR - basically, the Blummy is like a Greasemonkey script - it uses DOM manipulation to alter the page you're on, building up the container of all the Blummlets, and interacts with other sites using standard HTTP requests.)
* **Plans for Blummy**, [its use of Lazy Registration](http://ajaxpatterns.org/Lazy_Registration), security issues.
* Developing for **cross-browser compatibility**.
* Passing data from another domain with **JSON**.
* **The design behind Bandnews.** Most band websites don't bother with RSS, so Bandnews creates its own RSS feed, which is what the browser script reads.
* **Why some Ajax apps** are slow and what can be done about it.
* Libraries mentioned: [dojotoolkit](http://dojotoolkit.com), [prototype](http://prototype.conio.net).