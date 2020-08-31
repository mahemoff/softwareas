---
id: 660
title: 'SimpleMessagePlugin: Unobtrusive TiddlyWiki Status Message'
date: 2009-10-03T00:06:27+00:00
author: admin
layout: post
guid: http://softwareas.com/simplemessageplugin-unobtrusive-tiddlywiki-status-message
permalink: /simplemessageplugin-unobtrusive-tiddlywiki-status-message/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "378680706"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - Osmosoft
  - Project
  - TiddlyWiki
---
To simplify TiddlyGuv message rendering, I made "SimpleMessagePlugin". It removes the message box 1 second after a message was shown (using displayMessage). In the event another message appears in that time, it appends the message (as it normally does) and extends the message box's lifetime by a second. In other words, it always closes a second after the last message was shown. The algorithm is a pretty similar throttling deal as <a href="http://ajaxify.com/tutorial/">Ajaxagram</a>. 

<a href="http://tiddlywiki.mahemoff.com/SimpleMessagePlugin.html">Demo here</a>.

Latest version from <a href="http://trac.tiddlywiki.org/browser/Trunk/contributors/MichaelMahemoff/plugins/SimpleMessagePlugin?rev=10845">SimpleMessagePlugin</a>.