---
id: 555
title: 'Making a Bookmarklet: A Challenge on All Fronts'
date: 2009-07-02T16:32:49+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=552
permalink: /making-a-bookmarklet-a-challenge-on-all-fronts/
dsq_thread_id:
  - "375574276"
categories:
  - SoftwareDev
tags:
  - Bookmarklets
  - Javascript
  - Scrumptious
  - Usability
---
<a href="http://scrumptious.tv">Scrumptious</a>, a social bookmarking/comments app I began building recently, has a bookmarklet.

<img src="http://img.skitch.com/20090702-kay98b52eyfejr3ahk6374fqpp.jpg" style="width: 400px;" />

The bookmarklet is added from the demo homepage.

<img src="http://img.skitch.com/20090702-jjuym8p47ftg8e31fubspjx22h.jpg" />

It's not the first time I've made a bookmarklet for a website, the first time being <a href="http://webwait.com">WebWait</a>. 

<img src="http://img.skitch.com/20090702-ni29raysqmc7bsaqhn17a5kg1k.jpg" style="width:400px;" />

I found the Scrumptious edition more challenging though, for several reasons. This brief article outlines the challenges. Some I've solved to an extent, but all need further work.

<h3>Launch UI Challenge</h3>

The most obvious challenge is, how do you explain to users what they can do with a bookmarklet. Most users aren't geeks and I suspect most people still haven't heard of bookmarklets. Or what are sometimes called "favelets", since IE users have favourites, not bookmarks, which further highlights the problem. Here, I've explained with some text, but it ideally needs a diagram and perhaps a link to a separate page with a more detailed explanation, alongside a video.

<h3>Overlay UI Challenge</h3>

The next obvious challenge is UI design of the comments overlay. We're overlaying comments onto a page. One of the issues was using a z-index that's higher than what's on the site, hence my article on <a href="http://softwareas.com/whats-the-maximum-z-index ">max z-index</a>. Other questions too. How much transparency, if any? What kind of positioning and scrolling, and how wide should it be?

<h3>Coding Challenge</h3>

Bookmarklets need to be fairly small. IE6 limits you to <a href="https://www.squarefree.com/bookmarklets/limits.html">just 508 characters</a>, so if you are doing anything remotely interactive, you'll need to make the bookmarklet pull in a script from elsewhere, using <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a>. This is a good practice anyway (as <a href="http://www.blummy.com/">bookmarklet guru</a> <a href="http://alexander.kirk.at/">Alex Kirk</a> explained to me a while ago) because it means you can always update the app. The downside is you still have to be quite concerned about size, as you want the bookmarklet to come into effect straight away. For this reason, I wrote the Scrumptious bookmarklet without using JQuery, which meant going back to Javascript 101, and lots of ugly low-level DOM manipulation therein.

<h3>Deployment Challenge</h3> 

While there are various websites that let you <a href="http://ted.mielczarek.org/code/mozilla/bookmarklet.html">cut-and-paste Javascript code to build a bookmarklet</a>, I wanted to automate the process. <a href="http://en.wikipedia.org/wiki/Continuous_integration">Continuous integration</a>, Automated Deployment, and all that. Luckily, John Gruber has a <a href="daringfireball.net/2007/03/javascript_bookmarklet_builder">bookmarklet builder perl script</a>. I yoinked and tweaked it so that I could keep the Scrumptious bookmarklet in its own form.

Another issue is the URL of the Javascript which the bookmarklet requests. Since Scrumptious can run on different servers, this URL will change depending on where the server is stored. Right now, there's no server-side processing - all server-side content is static HTML. So I wrote a shell script to set the bookmarklet which any site operator could use.

<h3>Modularity Challenge</h3>

A bookmarklet is not the only place Scrumptious injects itself into the page. There's also a Greasemonkey script under construction, and I've experimented with <a href="https://jetpack.mozillalabs.com/">JetPack</a>. I'll also be building support for a site toolbar, so that an intranet operator could let you click on a "comments" link and inject Scrumptious comments on the page (so that users don't have to bother installing the bookmarklet, at least to comment on intranet sites).  The bookmarklet script has to be flexible enough to cover these subtly different scenarios. For example, the Greasemonkey script wants the comments overlay to be closed initially with a small button to launch it; the bookmarklet wants it to be open initially; and the Jetpack and toolbar want it to be off altogether until its explicitly launched.
