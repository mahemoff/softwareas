---
id: 244
title: An Ajax Framework a Day!
date: 2005-11-29T01:11:08+00:00
author: admin
layout: post
guid: http://www.softwareas.com/an-ajax-framework-a-day
permalink: /an-ajax-framework-a-day/
dsq_thread_id:
  - "375572770"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Frameworks
  - Libraries
  - Links
  - Patterns
  - Web
  - Wiki
---
**Today's Ajax framework is [JsRia](http://ajaxpatterns.org/Ajax_Frameworks#JsRia_.28Under_development.3B_from_June.2C_2005.29).** Yesterday's was **[ZK](http://ajaxpatterns.org/Ajax_Frameworks#ZK_-_Simple_and_Rich)**, with the Backbase entries updated too. **In the past week, there were Smartclient, Ajax JSP Taglib, Ajax JSF Framework, Cajax. [Here's the diff](http://ajaxpatterns.org/wiki/index.php?title=Ajax_Frameworks&diff=4223&oldid=4196).** The [week prior to that](http://ajaxpatterns.org/wiki/index.php?title=Ajax_Frameworks&diff=4223&oldid=4196) saw introduction of XOAD, Rialto, and Lotus Notes info.

**Have the [Ajax frameworks](http://ajaxpatterns.org/Ajax_Frameworks) entered the enlightened age of singularity?** (I've been listening to a lot of Ray Kurzweil podcasts lately, forgive me.) To some extent, yes, there is some pretty explosive growth here, because **several of these frameworks really have been released in the past couple of weeks**, as far as I can tell. In addition, many of the project owners and users have presumably become aware of the page, and seek to add their project or update my original description.

**So I'm thinking the frameworks page needs to be split before it bursts at the seams, what do you reckon?** I wish there was a way to keep them all on the same page, with a bit more Ajaxy dynamism, to let you manage and personalise things better. **As I alluded to [yesterday on Ajaxian](http://ajaxian.com/archives/2005/11/gollum_wikipedi.html), of all the Ajax projects being announced - wikis are somewhat lacking**. Surprising to me, since it was one of the most obvious Ajax examples to me - one I mentioned in the original [Ajax Podcast](http://softwareas.com/Ajax-Podcast), and one of the first [proof-of-concept demos](http://ajaxify.com/run/wiki) I created for the patterns. **One thing I'd like to see is wikis take more of a web service approach - let a thousand Ajax/Flash/Desktop wikipedia clients bloom. Sure, there are mashups now, but they're mostly read-only, and require manual scraping.** The idea I had with the [Ajax Patterns Reader](http://ajaxify.com/run/reader/logging/real) was to eventually let people leave feedback. There's another demo - [the portal](http://www.ajaxify.com/run/portal/drilldown/syncLinks/), which grabs content from ajaxpatterns.org, and there will be a further demo coming soon. To do all that properly, I'll likely create a web service to expose the wiki content as an RESTful API.

In closing off this tangent, here's a question: **How would it be creating a wiki from the ground up, with no UI? Just a collection of web services for managing content.** I've found MoinMoin is more configurable and pluggable than most, but it still starts with the unnecessary premise that the UI lives in the same process as the content.