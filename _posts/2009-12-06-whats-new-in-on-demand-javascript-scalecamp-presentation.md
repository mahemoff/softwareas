---
id: 739
title: 'What&#8217;s New in On-Demand Javascript? ScaleCamp Presentation'
date: 2009-12-06T18:02:53+00:00
author: admin
layout: post
guid: http://softwareas.com/whats-new-in-on-demand-javascript-scalecamp-presentation
permalink: /whats-new-in-on-demand-javascript-scalecamp-presentation/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "389952627"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Javascript
  - Presentation
  - ScaleCamp
---
<div style="width:425px;text-align:left" id="__ss_2660691"><a style="font:14px Helvetica,Arial,Sans-serif;display:block;margin:12px 0 3px 0;text-decoration:underline;" href="http://www.slideshare.net/mahemoff/on-demand-javascript-scalecamp" title="On Demand Javascript - Scalecamp 2009">On Demand Javascript - Scalecamp 2009</a><object style="margin:0px" width="425" height="355"><param name="movie" value="http://static.slidesharecdn.com/swf/ssplayer2.swf?doc=on-demand-javascript-scalecamp-091206105937-phpapp02&stripped_title=on-demand-javascript-scalecamp" /><param name="allowFullScreen" value="true"/><param name="allowScriptAccess" value="always"/><embed src="http://static.slidesharecdn.com/swf/ssplayer2.swf?doc=on-demand-javascript-scalecamp-091206105937-phpapp02&stripped_title=on-demand-javascript-scalecamp" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="355"></embed></object><div style="font-size:11px;font-family:tahoma,arial;height:26px;padding-top:2px;">View more <a style="text-decoration:underline;" href="http://www.slideshare.net/">presentations</a> from <a style="text-decoration:underline;" href="http://www.slideshare.net/mahemoff">mahemoff</a>.</div></div>

These are the slides from my ScaleCamp presentation, covering various techniques for various styles of On-Demand Javascript, including <a href="http://softwareas.com/design-pattern-script-islands">Script Islands</a>, "async" and "defer" attributes, and library support.

One of the interesting things at ScaleCamp is that many of the folks there are dealing with third-party advertisers and analytics providers. This leads to very different on-demand Javascript drivers from those of us mostly dealing with enterprise web apps. If you're a small fish in a big pond, you're pretty much held hostage to the script tags of leading advertisers and trusted analytics companies in your industry; if they serve the script slowly, it blocks your page from loading and therefore messes with user experience. That's why some of these new techniques are so critical, notably the dynamic async script tag technique <a href="http://ajaxian.com/.../google-analytics-unblocks-the-web-w-async-support">the Google Analytics came out with</a> at a very timely moment, just a couple of days before this presentation.