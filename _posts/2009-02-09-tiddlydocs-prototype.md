---
id: 518
title: TiddlyDocs Prototype
date: 2009-02-09T12:28:53+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=515
permalink: /tiddlydocs-prototype/
dsq_thread_id:
  - "384173835"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - Osmosoft
  - TiddlyDocs
  - TiddlyWiki
---
Simon McManus has <a href="http://simonmcmanus.wordpress.com/">overviewed TiddlyDocs</a>, a TiddlyWeb-based document editing and collaboration tool. It's a great example of taking an existing framework - TiddlyWiki - adding in a bunch of components - TiddlyWiki plugins and other open source pieces - and putting some custom code around it to generate something useful in just a few weeks. Simon's article has a good overview of all the moving parts inside TiddlyDocs.

I recorded a screencast to demo the initial version:

<object width="400" height="300"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=3109248&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=3109248&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><br /><a href="http://vimeo.com/3109248">TiddlyDocs - Early Prototype</a> from <a href="http://vimeo.com/user960717">Michael Mahemoff</a> on <a href="http://vimeo.com">Vimeo</a>.

I'm excited about the potential of this tool. In the simplest case, you can see it as an online word processor which, being open source, could therefore be deployed flexibly securely and freely behind any organisation's firewall. But it can be much more than just a word-processor, because each section is a tiddler behind the scenes, and is therefore a first class data structure with its own set of fields. In particular, there are the seeds of a workflow system, with a field indicating the current completion status, and another field assigning the individual who will progress it. This means you can get an RSS feed, for example, of all sections in "under review" status, or a list of all sections assigned to a particular user.