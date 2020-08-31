---
id: 417
title: Dynamic Favicon Library Updated
date: 2008-01-31T01:51:56+00:00
author: admin
layout: post
guid: http://www.softwareas.com/dynamic-favicon-library-updated
permalink: /dynamic-favicon-library-updated/
dsq_thread_id:
  - "375284196"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Favicon
  - HTML
  - Javascript
  - Links
  - Web
  - Web 2.0
---
<tags>Ajax, AjaxPatterns, Favicon, HTML, Javascript, Web, Web 2.0</tags>

I updated the favicon library a while ago, for a couple of projects I haven't released for various reasons. Anyway, <a href="http://www.hawksworx.com">Phil</a> asked me about it, so I thought it's a good time to package it up and release it properly. And in the process wrote up <a href="http://www.softwareas.com/taking-browser-tabs-seriously">Taking Browser Tabs Seriously</a> which has also been on the backburner.

The main point of this library is to update the favicon via Javascript, but at a higher level, its main objective is to provide some support for notifying the user of events in another tab. For example, if you start playing music in another tab, you can make a one-liner call to change the favicon to a sound. Or if you really need to alert the user, you can start animating it.

See <a href="http://softwareas.com/dynamic-favicons">the original post</a> for more info. The new features are:
<ul>
  <li><strong>Scrolling title.</strong> The window/tab title scrolls. (Title blink is coming. No, really!)</li>
  <li><strong>Stop functions.</strong> unanimate() and unscroll() will stop animation and scrolling, respectively. Previously you had to do stop animation indirectly, by calling change().</li>
  <li><strong>Rails/Scriptaculous style options</strong> Changed config to be fn(mainarg, optionalHash). Read the library or demo source to see the details.</li>
</ul>

Demos:
<ul>
  <li><a href="http://www.ajaxify.com/run/favicon/scroll/">Scrolling Favicon Demo</a></li>
  <li><a href="http://www.ajaxify.com/run/favicon/scroll/favicon.js">Scrolling Favicon Library</a></li>
</ul>

API (also in the code):
[javascript]
    favicon.change("/icon/active.ico", "new title"); // Cancels any animation/scrolling
    favicon.change("/icon/active.ico"); // leaves title alone. Cancels any animation.
    favicon.change(null, "new title"); // leaves icon alone. Cancels any scrolling.
  
    favicon.animate(["icon1.ico", "icon2.ico", ...]);
    favicon.animate(["icon1.ico", "icon2.ico", ...], {delay: 500} );
      // Tip: Use "" as the last element to make an empty icon between cycles.
      // Default delay is 2000ms
    // animate() cancels any previous animation

    favicon.scrollTitle("new title");
    favicon.scrollTitle("new title", { delay: 200, gap: "------"} )
      // delay is delay between each scroll unit
      // gap is string appended to title (default: "      ")
    // scrollTitle() cancels any previous scrolling
  
    favicon.unscroll();

    favicon.unanimate();
[/javascript]

Maybe in another two years, I'll update it again. The main enhancement would be to combine it with audio notifications (<a href="http://www.ajaxonomy.com/2008/ajax/cross-browser-sound-flash-only-as-a-last-resort">with or without Flash</a>, depending on the browser). So you could make a single call that (a) changes favicon; (b) scrolls the title; (c) plays a sound. Now that will get their attention!!!<!--e6c2551d3167c5c8ab2ebf4fb25a4bfb-->