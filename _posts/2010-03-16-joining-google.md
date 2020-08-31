---
id: 801
title: Joining Google
date: 2010-03-16T11:48:21+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=801
permalink: /joining-google/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375204777"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Google
  - html5
  - Javascript
  - Navel-Gazing
---
I mentioned I'm moving on from Osmosoft <a href="http://softwareas.com/twelve-days-of-tiddlywiki-twelve-days-of-osmosoft">a few weeks ago</a> and after <a href="http://12days.osmosoft.com">12days</a> and a week of doing much less than one could ever have imagined, it's time to announce where I'm going: Google. I'll be joining Google as a Chrome developer advocate, which means focusing on HTML5, Javascript, the Chrome browser, ChromeOS, and related technologies.

I'm very excited about the role, for reasons best explained in terms of a timeline for the web. I see the history of web technologies divided into three phases and I believe we're currently in the transition from the second to the third phase. Which is the starting context for this role.

<h3>Dark Ages (Web as a Black Art)</h3>

<p><img src="http://upload.wikimedia.org/wikipedia/commons/b/b6/French-gendarme.jpg" width="200" /></p>

<p>Rich web apps were hard work. Black art even. During this phase, I spent most of my time on server-side languages - Perl, PHP, Java/J2EE - and Javascript was a weird sideline. Taking an interest in the user experience, I always wanted to know more about this black art, since it's the web technologies that touch the user and have the most direct influence over their experience with any application. But what paid the bills in the late '90s and early noughties was form submissions and page refreshes. And most Javascript content was odd little ticker tape scripts you could download, not too much to learn from, and always difficult to achieve in one's spare time. I think this was the frustrating experience for many web developers: not enough time and hard work. I did get by and pick up a few tricks here and there, but things only took off when the A-word was unleashed ...</p>

<h3>Ajax Era (Web as an Established Practice)</h3>

<img src="http://farm3.static.flickr.com/2112/2368225695_7f87aaedba.jpg" width="200" />

<p>Everything changed five years ago, on February 18, 2005. Jesse James Garrett hopped in the shower, came up with the term "Ajax", and published his thoughts on this rising architectural pattern. Many people bristle at the notion that a simple term, for something people were already doing, can make such an impact. "BUT I already knew how to do that!" they cry. Good for them. But the fact is, Ajax allowed the whole developer community to rally around this style of application. Events, blogs, books, libraries, tools, the whole thing flourished. I got seriously interested, <a href="http://softwareas.com/ajax-podcast">recorded a podcast explaining the topic</a>,  and started diving into all the existing applications, which ultimately led to <a href="http://ajaxpatterns.org">the Ajax Patterns wiki</a>. All those applications, and many featured in the book, were created in the Dark Ages by brilliant pioneers who had scant resources to learn from. Today, such applications can be created at exponentially faster rates. This is thanks to improved knowledge, improved libraries, and improved tools.</p>

<p>There are historical analogies to this era, e.g. the rapid rise of the automobile industry once all parts were in place. In that case, it was more a matter of discovering new physical and engineering principles, whereas with Ajax, it was a superficial act. The browsers were already there, with a killer feature like IE's XMLHttpRequest sitting largely unnoticed for five years. Few people had taken the time to really understand how they worked. It was the Ajax term to trigger the boom.</p>

<h3>HTML5 Era (Web on an Improved Platform)</h3>

<a href="http://www.flickr.com/photos/neatocoolville/140303972/"><img width="200" src="http://farm1.static.flickr.com/54/140303972_dc5fa8a7bd.jpg" /></a>

<p> (I hesitate to call this the era of HTML5, as many things happening are outside HTML5, notably improvements to CSS and the core Javascript/ECMAscript language. But HTML5 is increasingly becoming <a href="http://www.quirksmode.org/blog/archives/2010/03/html5_apps.html">a brand</a>, much like Ajax in its heyday, a term that's familiar to anyone with a passing interest in technology.)</p>
<p>The starting point for this era is the success of open web technologies. While we continue to learn more each day, we have the basics in place today. We know how to harness HTML, CSS, Javascript to make powerful libraries and  applications on the existing browsers. This is where the Ajax Era landed us. We have seen some genius hacks. In fact, we have seen MANY ingenius hacks. <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript and JSONP</a>, for example, are completely fundamental to the way business is done on the web these days, and is utterly a hack. Full credit to those who came up with them, but these hacks can only go so far. They can increase programming complexity, impact on performance, and cause security threats for those not fully-versed in their capabilities. And that's just for the things we <em>can</em> do. The bigger problem is that we are heavily limited in our functionality on Ajax-Era technologies. We can't do rich graphics or video, for example. So the next stage is all about improving the underlying platform. It's not something an application programmer,  however heroic, can do on their own. It's something that has to involve improvements from the platform providers, i.e. the browser manufacturers and others.</p>
<p>To draw a line in the sand, take IE6. Although <a href="http://ie6isolderthanyourgrandpa.com">it was created back in 2001</a>, we could do far more with it in 2004 (e.g. Google Maps) than we could in 2001, and we can do far more with it in 2010 than we could in 2004. This is because of all the knowledge, libraries, and tools the Ajax Era has provided. <strong>However, we're in serious plateau mode now. We can continue to squeeze out 1-percenters, but the low-hanging fruit was plucked and digested a long time ago. The next stage has to be an improvement to the underlying platform, and that's what's going on today with modern web browsers.</strong></p>
  <p>Once you say "okay we're now going to build the next-gen web platform", you're not just going to add support for round corners. So there's been a truckload of effort going on, in HTML5 and beyond. Graphics in the form of canvas and SVG and WebGL and CSS3, media in the form of audio and video tags, semantic markup improvements, new form controls, offline storage, support for location-awareness. And much more.</p>
  <p>We have the new platform and alongside it, we have the activity of understanding how to use the new platform. Not just understanding the parts, but the whole. How do you put all these things together in meaningful ways. Can we show custom-font text on a canvas? If so, how? And when does it make sense?  And how to avoid performance problems? Or, to take another example, what kind of CSS transforms can we use to render videos? And since we can grab image data from the videos, what are some cool things we can do with that data? And all the while, where's the graceful degradation story here? How do these apps look in older browsers? Most of the talk so far has been on the capabilities of the platform, not patterns of usage.</p>
  <p>All these new capabilities take us to the place we've been aiming for all along: <a href="http://softwareas.com/ajax-lite-versus-ajax-deluxe">true applications deluxe</a>, not just "html++". Of course, there's plenty of room for both of these, but we're now in a place where we can really build true applications with all the capabilities of a traditional native experience. We're seeing it in a big way in mobile space. The new model is all about sandboxing, doing away with the filesystem, and explicit permissions. Exactly what the web's good for. They're not only a good fit technically, but they've become the ubiquitous lingua franca among the programming community. The technologies are familiar, as are the patterns of UI design and code composition. Those patterns will continue to evolve with HTML5 and associated technologies.</p>
<p>We're just scratching the surface here; there are exciting times ahead!</p>

----

I'm not an official Googler yet, nor even a Noogler, as I've taken time off to chill, smell the roses, and pursue a few projects (like <a href="http://twitter.com/mahemoff/status/10534324953">dusting off</a> the <a href="http://mahemoff.com">homepage</a> and ... watch this space. Actually, watch <a href="http://twitter.com/mahemoff">that</a> space). I'm starting in about a month. And of course, even when I am official, this blog continues to be my own opinions, caveat emptor yadda.

The role covers EMEA and I'm still based in London. Despite not starting just yet, I'm looking forward to participating in <a href="http://www.london-gtug.org/Venue">tonight's Chrome/Chromium OS and HTML5 London event</a>. See you there!

(<a href="http://www.techmeme.com/100315/p10">I'm not the only one to announce a move to Google at this time.</a> I'm looking forward to meeting and working with many of my talented future colleagues.)