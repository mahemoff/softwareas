---
id: 735
title: 'Design Pattern: Script Islands'
date: 2009-12-06T17:47:29+00:00
author: admin
layout: post
guid: http://softwareas.com/design-pattern-script-islands
permalink: /design-pattern-script-islands/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574529"
categories:
  - SoftwareDev
tags:
  - Ajax Patterns
  - Design Patterns
  - Javascript
  - Performance
  - Presentation
---
<img style="width:400px;" src="http://picupper.com/2009/12/06/car-on-island_sale.jpg" />

"Script Island" is what I'm calling a design pattern I <a href="http://mini.softwareas.com/experiment-making-use-of-and-innerhtml-with-s">alluded to here</a>. The pattern is to embed Javascript in your HTML like so:

[html]
<script id="greeting" type="x-deferred-script">
  alert("this is my script - it's eval'd on demand");
</script>
[/html]

When the page loads, the browser should say "I don't know what 'x-deferred-script' is, and therefore ignore the concents of the script tag. You eval it manually later on, using something like <tt>eval($("script#greeting").html());</tt> This is similar to <a href="http://googlecode.blogspot.com/2009/09/gmail-for-mobile-html5-series-reducing.html">Google's trick of embedding Javascript in comments</a>, but has the additional benefit of keeping Javascript where it should be, in a script tag. This way, it plays nicer with code editors (e.g. Vim happily handles syntax highlighting) and analytical tools. (Technically, those tools should probably do the same as browsers and *not* treat anything inside a script tag as Javascript, but fortunately for us, they do.)

Script Islands are useful in the following situations:

* With a complex web app - lots of Javascript - where you want it to load quickly and without lots of processing or round-tripping back to the server. Sometimes, it's a better user experience to load the lot in one go, show something, and eval() the rest of the Javascript once the basic app is running (perhaps in anticipation of a separate "page" or another part of the application). This is a special case of <a href="http://ajaxpatterns.org/Predictive_Fetch">Predictive Fetch</a>; it makes sense Google would use (a variant of) Script Island for the mobile edition of GMail, where round trips to and from the server are expensive.
* With a single-page application (SPA) like TiddlyWiki, where all the code is inside the HTML file. Each of the script islands is a separate module, and a microkernel is responsible for loading the scripts according to different rules. For example, the scripts might contain "depends" attributes to declare they depend on other scripts, so the microkernel sequences the script loading. Or another scenario might be that the user has some control over which scripts get loaded; instead of deleting the other scripts from the file, you keep them around in case the user wants to repackage the SPA, with a different set of scripts.

BTW I <a href="http://mini.softwareas.com/experiment-making-use-of-and-innerhtml-with-s">originally</a> used <tt>&lt;script src=""&gt;</tt> to trick the browser into not evaluating the script tag's innerHTML. Thanks to <a href="http://jermolene.com">Jeremy</a> for coming up with the more elegant alternative of a <tt>type=x-tiddler</tt> (which I stated above in the more generic form <tt>type=x-deferred-script</tt>).