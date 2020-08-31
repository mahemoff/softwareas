---
id: 704
title: 'Embedded Images in TiddlyWiki Under IE6 via MHTML &#8211; Proof-of-concept'
date: 2009-11-16T21:32:38+00:00
author: admin
layout: post
guid: http://softwareas.com/embedded-images-in-tiddlywiki-under-ie6-via-mhtml-proof-of-concept
permalink: /embedded-images-in-tiddlywiki-under-ie6-via-mhtml-proof-of-concept/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574511"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Experiment
  - Graphics
  - Javascript
  - MHTML
  - TiddlyWiki
---
<a href="http://tiddlywiki.mahemoff.com/graphical.html" title="tiddlywiki mhtml images (by mahemoff)"><img src="http://farm3.static.flickr.com/2655/4109725075_f297009308.jpg" title="tiddlywiki mhtml images (by mahemoff)" alt="tiddlywiki mhtml images (by mahemoff)" width="400" height="338" /></a>

I only came across the <a href="http://www.phpied.com/mhtml-when-you-need-data-uris-in-ie7-and-under/">MHTML image hack</a> over the weekend, while listening to @jeresig on the new <a href="http://blog.jquery.com/2009/11/13/announcing-the-official-jquery-podcast/">jQuery podcast</a> (incidentally not the only <a href=""http://paulirish.com/2009/introducing-yayquery-a-jquery-podcast">jQuery podcast</a> to be launched in the past week or two).

The MHTML image hack lets you embed images with text, just like ye olde data: URI hack, but in a way that works for IE6. MHTML is MIME for HTML.

Of course, I immediately wondered if it could work in a single-page web app like tiddlywiki, and it turns out it can, though my quick exercise still has some problems.

<a href="http://tiddlywiki.mahemoff.com/graphical.html">IE6 TiddlyWiki images demo here</a>

As I wrote on the demo itself:

<blockquote>
<p>Normally, images are contained in a separate location, pointed at from HTML IMG tags or from CSS background-image properties. However, Tiddlywiki is a style of web app where everything resides in one file. So how to include images?

<p>The usual hack is to embed data: URIs (http://en.wikipedia.org/wiki/Data_URI_scheme). However, no go for IE6 and IE7. Hence, a "newer" technique - newer meaning recently discovered. That is, MHTML (http://www.phpied.com/mhtml-when-you-need-data-uris-in-ie7-and-under/).

<p>I was curious if MHTML worked in single-file HTML pages, reading off a file URI, and to my surprise it does. That said, it's not perfect at all. Firstly, I had to hard-code the location, because I don't know how to refer to "the current file" within the MHTML link. (I suppose a workaround would be to output the image file and refer to that with a relative URL, but we lose the benefit of everything being in one file.) Secondly, I played around with various base-64 images and this arrow one (from the phpied.com demo) was the only that worked :(.

<p>So it's a proof-of-concept with many gaps left for the reader to fill!
</blockquote>

Hopefully people play with this further. <a href="http://ie6isolderthan.com">At 3002 days old and counting</a>, your grandpa's browser isn't going anywhere fast.