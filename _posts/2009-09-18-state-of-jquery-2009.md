---
id: 638
title: State of jQuery 2009
date: 2009-09-18T08:08:21+00:00
author: admin
layout: post
guid: http://softwareas.com/state-of-jquery-2009
permalink: /state-of-jquery-2009/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "384419628"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - JQuery
---
<a href="http://twitter.com/FND">Fred</a> noticed Jon Resig's State of jQuery slides are up:

<div style="width:425px;text-align:left" id="__ss_2006198"><a style="font:14px Helvetica,Arial,Sans-serif;display:block;margin:12px 0 3px 0;text-decoration:underline;" href="http://www.slideshare.net/jeresig/state-of-jquery-09" title="State of jQuery &#39;09">State of jQuery &#39;09</a><object style="margin:0px" width="425" height="355"><param name="movie" value="http://static.slidesharecdn.com/swf/ssplayer2.swf?doc=state-of-jquery-09-090916091836-phpapp02&stripped_title=state-of-jquery-09" /><param name="allowFullScreen" value="true"/><param name="allowScriptAccess" value="always"/><embed src="http://static.slidesharecdn.com/swf/ssplayer2.swf?doc=state-of-jquery-09-090916091836-phpapp02&stripped_title=state-of-jquery-09" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="355"></embed></object><div style="font-size:11px;font-family:tahoma,arial;height:26px;padding-top:2px;">View more <a style="text-decoration:underline;" href="http://www.slideshare.net/">documents</a> from <a style="text-decoration:underline;" href="http://www.slideshare.net/jeresig">jeresig</a>.</div></div>

Highlights for me:

Now:

* Now using sizzle, the quick, generic (not just JQuery), selector engine. Slide 8 show
s almost 2* performance improvement on IE6 from JQuery 1.2.6 -> 1.3.2.
* Performance improvements are apparently dramatic (browser averages):
 * width() / height() ~4* speedup (good - I need these for http://caption.im8ge.com)
 * hide() / show() ~3* speedup (good - I use them everywhere!)
 * element insert: : ~6* speedup (likewise)
* <a href="http://testswarm.com">Test Swarm</a> is go! Awesome, Awesome initiative. I hope we take advantage of it for TiddlyWiki testing, once it extends to other frameworks. (Or make something similar.)

* Ridiculous growth and market share (p15-17), and new big sites using JQuery (p13): Whitehouse, Wikipedia, Amazon, Microsoft. Not too shabby eh. Stuff like this makes it much easier for advocates to sell in their organisations.
* Setting up private CDN on Media Temple, who's donating all the resources.

Future:

* <strong>More performance improvements in 1.3.3</strong> - p23 shows 3.5x improment over 1.3.2! (perhaps for a subset, but it's still a big and useful set).
* JQuery builds <strong>optimised for mobile</strong>.
* Moving <strong>parts of JQuery UI widget -> core</strong>.
* Four conferences in 2009 - online, <strong>London</strong>, SF, Boston.
* Better community sites, inlcuding online forum. Plugin site rewrite. 
* <strong>All plugins on CDN.</strong>.
* Core -> Github.