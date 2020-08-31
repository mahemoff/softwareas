---
id: 607
title: Modal Dialog JQuery Plugin
date: 2009-08-27T16:03:46+00:00
author: admin
layout: post
guid: http://softwareas.com/modal-dialog-jquery-plugin
permalink: /modal-dialog-jquery-plugin/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375342696"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - JQuery
  - Lightbox
  - Plugin
  - Project
---
<a href="http://twitter.com/mahemoff/status/1640629729"><img style="width:400px;" src="http://img.skitch.com/20090827-fd8efw4bp1bp8b85y84t93d9tf.jpg" /></a>

This has been a while coming, but I made a little "yet another modal dialog lightbox JQuery plugin" thing this week.

<a href="http://project.mahemoff.com/modal/">Demo and Download for Modal Dialog - JQuery Plugin</a>

It was driven by <a href="http://tiddlydocs.com">TiddlyDocs</a>, but I've been wanting one anyway for a while. Mostly because lightbox libraries generally do some hocus-pocus on page load, like applying to everything marked rel="lightbox", but don't let you dynamically produce the lightbox yourself. That's fine for pages that are just a static image gallery, but not useful to someone building a dynamic web app.

I've subsequently used <a href="nyromodal.nyrodev.com/">nyromodal</a>, <a href="http://twitter.com/mahemoff/statuses/1647793685">on good advice</a>, but wanted something smalller and with a simple API for my main use case, which is just showing some text.

The plugin also simplifies work by not requiring you to install a separate CSS file. Doing that, and linking to it, as well as installing any images, is something that always slows me down when I want to start using a graphical client. In keeping with the "happy path" You-Aint-Gonna-Need-It (YAGNI) mantra, I'd rather keep a library to a single Javascript file - be evil and do styling in the library by default, but still support users who want to put custom CSS in a stylesheet.

<img style="width:400px;" src="http://img.skitch.com/20090827-qqk7a963e6f3j758fntauu7nh2.jpg" />