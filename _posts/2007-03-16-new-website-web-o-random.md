---
id: 368
title: 'New Website: Web-O-Random'
date: 2007-03-16T11:55:26+00:00
author: admin
layout: post
guid: http://www.softwareas.com/new-website-web-o-random
permalink: /new-website-web-o-random/
dsq_thread_id:
  - "375503972"
categories:
  - Links
  - SoftwareDev
tags:
  - Javascript
  - Links
  - Web-O-Random
  - Web2.0
  - Weborandom
---
<div id="digg">
  <script type="text/javascript"><!--
digg_url = 'http://weborandom.com';
// -->
</script>
<script src="http://digg.com/tools/diggthis.js" type="text/javascript"></script>
</div>

<a href="http://weborandom.com"><img src="/images/weborandom.png" width="400" height="320"></a>

I made a new Ajax toy. <a href="http://weborandom.com">Web-O-Random</a> is a random website finder with some Ajaxy goodness:

<ul>
<li>Sites load into a carousel (slider) component. Thanks to Bill Scott and Yahoo! for providing the original component and Sebastien Gruhier for the prototype port which is used here.</li>
<li>Pages load into an IFrame (as with <a href="http://webwait.com">WebWait</a>).</li>
<li>User can re-randomize, which leads to a JSON payload of new random sites.</li>
</ul>

<p>If you hunt for it, you'll find there's a way to search too, but I had to de-emphasise it as mysql full-text search takes 1-2 minutes to crunch through 4M (indexed) rows (each representing a website). If I have time, I may set up a reverse index table to cache results.</p>

<p>Initial reactions:</p>
<ul>
<li>"...?" This is the typical reaction. It may be interpreted as a polite version of Cartman's "Dude, this is pretty **** right here?" as in "Who would ever use this?". Sometimes people forget that not everything has to be as popular as Google...apps like Weborandom and Webwait can be coded in a few days and hosting costs are pretty trivial nowadays. As development time trends downwards to zero, it's the long tail of web apps! See <a href="http://www.toolshed.com/blog/articles/2005/09/15/what-happens-when-t-approaches-0">What Happens When t Approaches Zero?</a>
<li>"So I get a new site by clicking Randomize?" (You're meant to use the carousel first. I added some initial animation to the carousel, which looks cool and shows people there's more than meets the eye. I also made the carousel default to start in the middle instead of on the left.)
<li>"Are those your ads?" (He thought the carousel was adsense. I refactored by showing a boldfaced website title instead of a blue link).</li>
<li>"How do I click the arrow key? I can't see the cursor." (Confusing to have keyboard bindings in the absence of a textarea/input control. Changed the instruction text.)
</ul>
<object width="425" height="350"> <param name="movie" value="http://www.youtube.com/v/bZ9WhpQhv8g"> </param> <embed src="http://www.youtube.com/v/bZ9WhpQhv8g" type="application/x-shockwave-flash" width="425" height="350"> </embed> </object>