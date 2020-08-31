---
id: 182
title: Greasing Greasemonkey Scripts
date: 2005-08-21T00:30:51+00:00
author: admin
layout: post
guid: http://www.softwareas.com/greasing-greasemonkey-scripts
permalink: /greasing-greasemonkey-scripts/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572398"
  - "375572398"
categories:
  - Links
  - SoftwareDev
tags:
  - Browsers
  - Firefox
  - Greasemonkey
  - Links
  - Software
  - Web
---
**Tweaking a Greasemonkey script is easy. It's just a single file, so you download the file locally, edit it, and install it the same way you'd install any other script.**

I did this because I needed a quick fix for the super-helpful [XMLHttpRequest Debugging](http://blog.monstuff.com/archives/000252.html) script. Sometimes the console has a little trouble with positioning - using it with [Google Maps](http://maps.google.com) caused it to sit behind the upper portion of the page due to layering. So I made two quick fixes - increased the z-index in the embedded stylesheet so it would appear in front and also changed the default coordinates (I'd adjusted them with "about:config", but somehow that wasn't picked up.)

All in all, I was able to **tweak the script, not knowing anything about the GM API, and have it running in my browser in about 10 minutes. Had it been a standard Firefox extension, I would have been out of luck. I'd presumably have to download the original source, set up a dev/testing environment, and be able to package it all up including meta-info.** Furthermore, I'd have to restart Firefox to test it, unlike Greasemonkey which works straight away. I've never tried all that with extensions, but that's my perception from a little looking around.

I'm nowhere near as bullish as some about Greasemonkey, at least in the medium-term, as some people, because I think the whole Firefox extension mechanism is way too complex for most end-users, let alone the idea that you have to install Greasemonkey scripts on top of one of those extensions. But in any event, once you have the [Greasemonkey extenstion](http://greasemonkey.mozdev.org/) installed, it's a cinch to remould a script you come across.