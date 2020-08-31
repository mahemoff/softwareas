---
id: 561
title: TiddlyWeb-JQuery Comments Plugin
date: 2009-07-21T15:39:59+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=558
permalink: /tiddlyweb-jquery-comments-plugin/
dsq_thread_id:
  - "375197647"
categories:
  - SoftwareDev
tags:
  - JQuery
  - Osmosoft
  - Plugin
  - Project
  - tiddlyweb
---
<object width="400" height="300"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=5694409&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=5694409&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><p><a href="http://vimeo.com/5694409">TiddlyWeb-JQuery Comments Plugin - Screencast @ Vimeo</p>

I've extracted from <a href="http://scrumptious.tv">Scrumptious</a> a nested comments plugin you can integrate into any POJA (plain ol' Javascript app). You can find it here in the repo: <a href="http://trac.tiddlywiki.org/browser/Trunk/contributors/MichaelMahemoff/lib/comments">TiddlyWeb-JQuery Comments Plugin</a>.

As the <a href="http://trac.tiddlywiki.org/browser/Trunk/contributors/MichaelMahemoff/lib/comments/README">README</a> explains, usage is a one-liner once you've set it up. Just do $(selector).comments("topic"). The topic is an identifier for the set of comments; so that when the UI loads, it pulls down all comments with that ID in its "topic" field. Internally, topic acts as the root of the comments tree...but you don't really need to know that.

This plugin is a JQuery equivalent of <a href="http://tiddlywiki.mahemoff.com/CommentsPlugin.html">the TiddlyWiki comments plugin</a>, minus some of the more exotic options, and the ability to delete. Eventually, I hope to introduce those things, but only as the need arises - so if you're using this, please let me know how I can improve it.