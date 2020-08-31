---
id: 562
title: TiddlyWeb Now Reloads Code
date: 2009-07-21T21:58:25+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=559
permalink: /tiddlyweb-now-reloads-code/
dsq_thread_id:
  - "375574331"
categories:
  - SoftwareDev
tags:
  - tiddlyweb
---
<img src="http://picupper.com/2009/07/21/Cheetah.jpg" style="width:400px;" />

I've begun working on the server-side of TiddlyWeb a bit, mostly to make stuff degrade gracefully as I begin to build a <a href="http://softwareas.com/as-we-may-think-url-trails">Trails</a> facility into <a href="http://scrumptious.tv">Scrumptious</a>. In TiddlyWeb, an app-specific plugin is how you build an app on the server-side (or you can <a href="http://cdent.tumblr.com/post/141439434/tools-together">use a completely separate web framework</a> like Django or Rails, making server-to-server RESTful calls, but that's another story).

I <a href="http://groups.google.com/group/tiddlyweb/browse_thread/thread/5575ec3212dbb60b">asked about reloading code</a> on the group this week. I want to change my Python code and hit reload in the browser and see the changes. To me, this this kind of "hot deploy" during development is a must-have for any web framework. There's an argument that testing would render it unnecessary, but (a) it's difficult to write tests when you're learning and exploring an environment; (b) kool-aid aside, some things can't be tested or are Test-Driven Design is simply not the most productive way to develop it (it comes down to forces - a cost-benefit analysis); (c) functional and integration tests, working across the whole server, and reloading code on each request is an easy way to make those happen.

Anyway, Chris has kindly produced the necessary pieces.

Here's how I got it working. Here's what I did to get it working on Mac, which is slightly different from Linux setup:

* Download <a href="http://github.com/tiddlyweb/tiddlyweb-plugins/blob/b7705b1319ff99e5d717c59a70af8d39635c367c/reloader/reloader.py">reloader.py</a> and <a href="http://github.com/tiddlyweb/tiddlyweb-plugins/blob/b7705b1319ff99e5d717c59a70af8d39635c367c/reloader/wserver.py">wserver.py</a> stick them in top-level tiddlyweb instance directory.
* Introduce the following to your tiddlywebconfig.py: <tt>'twanager_plugins': ['wserver']</tt>. Note - do *not* try to use reloader as a plugin; it just needs to be in your directory as wserver uses it.
* Run the server using <tt>twanager wserver</tt>.

If you have browser caching on, you might need to hit shift-reload at times. I don't have caching on and it works fine with just reload. This is a big help, thanks Chris.