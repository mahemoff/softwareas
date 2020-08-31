---
id: 470
title: 'Shout &#8211; First TiddlyWiki Plugin'
date: 2008-08-05T19:50:39+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=467
permalink: /shout-first-tiddlywiki-plugin/
dsq_thread_id:
  - "375573900"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - Macro
  - TiddlyWiki
---
Okay, it's remarkably lame, but here's my first TiddlyWiki plugin. It defines a new <tt>shout</tt> macro - you include &lt;&lt;shout some-message&gt;&gt; in a tiddler and it includes A SHOUTING VERSION OF THE MESSAGE.

I adapted it from the sparklines plugin. The important code is at the end - you create a macro by defining a value <tt>config.macros.helloWorld</tt>, then you simply implement <tt>config.macros.helloWorld.handler</tt>. This function receives a <tt>place</tt> variable, defining where the macro will go, and the parameters that were passed into the macro (<tt>params</tt>).

(removed during jekyll conversion)
