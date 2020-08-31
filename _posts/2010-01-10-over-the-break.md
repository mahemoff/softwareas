---
id: 757
title: Over the Break
date: 2010-01-10T13:00:21+00:00
author: admin
layout: post
guid: http://softwareas.com/over-the-break
permalink: /over-the-break/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "418341233"
categories:
  - SoftwareDev
tags:
  - Navel-Gazing
---
<a href="http://project.mahemoff.com/snowman/snowman.html"><img style="width: 400px;" src="http://img.skitch.com/20100110-brgxkghw3ybd72e6thak355duk.png" /></a>

Quick mention of  projects and writings outside this blog:

<ul>
  <li>jQuery iFrame plugin - Stepped up work on this, as it was buggy and not very jQuery-plugin-like. <a href="http://github.com/mahemoff/jQuery-iFrame">Whacked it in GitHub</a> along with test cases. Not all are passing on <a href="http://www.ie6isolderthanyourgrandpa.com/">the 3058 day old browser</a>, yet. This was a good opportunity to play around with asynchronous testing in QUnit and I was pleasantly surprised to find there's good support for it - use stop() to suspend the test case (conceptually) and start() to continue it. <a href="http://github.com/mahemoff/jQuery-iFrame/blob/master/test/test.js">QUnit Asynchronous tests</a>.</li>
  <li>Scrumptious reboot - Following Osmosoft's decision to deploy everything inside a multi-user TiddlyWiki platform, Scrumptious has to be migrated to work inside of a TiddlyWiki. The final, pre-TiddlyWiki, <a href="http://trail.scrumptious.tv/podcasting/">Trails player</a> you can see online. I've since begun work on an overlay plugin, which is a <a href="http://en.wikipedia.org/wiki/Claytons">Claytons</a> TiddlyWiki: the TiddlyWiki you're having when you're not having a TiddlyWiki; there's a TiddlyWiki underneath for power-user functionality and a pretty generic UI on top of it. You can flip back and forth between a TiddlyWiki and a special overlay UI, which has full access to the TiddlyWiki state. It works by hiding all TiddlyWiki elements and pushing "style" elements to a DocumentFragment, so the operation can subsequently be reversed when flipping back.  The first <a href="http://trail.scrumptious.tv/TrailPlayer.html">proof-of-concept</a> is here (<a href="http://trac.tiddlywiki.org/browser/Trunk/contributors/MichaelMahemoff/plugins/TrailPlugin">source in the TW repo</a>). I'm psyched about this general approach for rapidly building web apps in a multi-user environment. TiddlyWeb provides a RESTful, permissioned, set of web services; and the UI can then be as flexible as you like. Ideally, each recipe/room would be in its own subdomain to help prevent XSS concerns.</li>
  <li>Mahemoff.com reboot - Okay, it still needs some love, but <a href="http://mahemoff.com">my homepage</a> is at least up-to-date now.
  <li>Server-Side Javascript article - Published <a href="http://www.readwriteweb.com/archives/server-side_javascript_back_with_a_vengeance.php">Server-Side Javascript: Back With a Vengeance</a>. Sums it all up really. I decided to submit it to ReadWriteWeb, rather than here or Ajaxian, because I figure i's a good thing to make the wider audience aware of trends like this. Otherwise, it's preaching to the converted to some extent.</li>
  <li>End of Days for "View Source" - An editorial musing about <a href="http://ajaxian.com/archives/the-end-of-days-for-view-source">the end of days for View Source</a>. Turns out there's going to be a SXSW panel on View Source and Alex Russell, who's participating, has <a href="http://alex.dojotoolkit.org/2010/01/view-source-is-good-discuss/>opined further</a> on the topic, and there's a <a href="http://saveviewsource.org">Save View Source</a> effort.
  <li>It's snowing and freezing in London, hence <a href="http://project.mahemoff.com/snowman/snowman.html">this Snowman mashup<a/> building on <a href="http://ajaxian.com/archives/web-2-snow">@webreflection's efforts</a>.</li>
</ul>
