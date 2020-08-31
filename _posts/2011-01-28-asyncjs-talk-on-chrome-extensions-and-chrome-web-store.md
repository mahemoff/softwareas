---
id: 1085
title: Async Talk on Chrome Extensions and Chrome Web Store
date: 2011-01-28T19:17:08+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1085
permalink: /asyncjs-talk-on-chrome-extensions-and-chrome-web-store/
dsq_thread_id:
  - "375574848"
categories:
  - SoftwareDev
tags:
  - Chrome
  - Javascript
  - Presentation
---
I gave a talk last night at <a href="http://asyncjs.com/ ">Async</a>, a fortnightly meetup for Brighton's ever-thriving JavaScript community, organised by the talented <a href="http://premasagar.com">Prem Rose</a>. The talk was on Chrome Extensions and the Chrome Web Store, and was a mashup of our separate <a href="http://gdd-2010.appspot.com">GDD talks</a> on those topics (<a href="https://github.com/PaulKinlan/GDD-2010">GitHub</a>), some live coding, and some new stuff now that the Web Store is live...though the main focus was Chrome extensions.

<a href="http://prez.mahemoff.com/async-chrome">Slide Deck: Chrome Extensions and the Chrome Web Store</a>

A fun part of the talk was live coding. I haven't done it before, but I felt it went well and was definitely worthwhile. The project was an extension to show the latest blog posts on the Async website, in a toolbar button (aka browser action). Chrome extensions are a lot easier to write than most people imagine, so it was an effective demo to start with a new directory and make it happen. For the record, here's the extension we hacked up in 15 minutes or so: <a href="http://prez.mahemoff.com/async-chrome/async.crx">async.crx</a>. (Styling was not the main focus of this exercise :) ).

I also did something I've been meaning to do for a while: A Venn diagram to illustrate the relationship between <a href="http://code.google.com/chrome/webstore/articles/apps_vs_extensions.html">extensions, packaged apps, and hosted apps</a>:

<img src="http://farm6.static.flickr.com/5256/5390822668_fe99179465_o.jpg" />

Finally, I had a good question about detecting if you're website is running as an installed app. I couldn't remember the details, but <a href="http://groups.google.com/a/chromium.org/group/chromium-apps/browse_thread/thread/3a9c85a059d205ed/2dda367e20d526c2">they are here</a>:

[javascript]
if (window.chrome && chrome.app && chrome.app.isInstalled)
[/javascript]

(Updated the snippet following Johan's suggestion in the comments.)