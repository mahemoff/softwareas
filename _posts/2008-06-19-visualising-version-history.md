---
id: 452
title: Visualising version history
date: 2008-06-19T08:50:39+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=449
permalink: /visualising-version-history/
dsq_thread_id:
  - "440564982"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Screencast
  - Version Control
  - Visualization
---
I'm a redundancy fanboy. In visualisation, different formats suit different personalities and different tasks. With version control, the usual format  is just a text log. This is good if you're scanning for specific terms, but pretty ordinary for other activities - e.g. to get a feel for general trends that have arisen, the pace of change, or the rise and fall of specific contributors.

It's encouraging, then, to see demos like the following, which shows the evolution of the Python language project (via <a href="http://twitter.com/dalmaer/statuses/838380219">Dion's tweet</a>).

<object width="400" height="302">	<param name="allowfullscreen" value="true" />	<param name="allowscriptaccess" value="always" />	<param name="movie" value="http://www.vimeo.com/moogaloop.swf?clip_id=1093745&amp;server=www.vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" />	<embed src="http://www.vimeo.com/moogaloop.swf?clip_id=1093745&amp;server=www.vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="302"></embed></object><br /><a href="http://www.vimeo.com/1093745?pg=embed&sec=1093745">code_swarm - Python</a> from <a href="http://www.vimeo.com/michaelogawa?pg=embed&sec=1093745">Michael Ogawa</a> on <a href="http://vimeo.com?pg=embed&sec=1093745">Vimeo</a>.

It reminds me of one of the first screencasts by Jon Udell, <a href="http://weblog.infoworld.com/udell/2005/01/22.html">a fascinating walkthrough of the evolution of a wikipedia page over a year or so</a>. The page he chose for this demo is as memorable as the message of the video itself.

<embed 
src="/files/jwplayer/mediaplayer.swf" 
width="300"
height="300"
allowscriptaccess="always"
allowfullscreen="true"
flashvars="file=http://weblog.infoworld.com/udell/gems/umlaut_media/umlaut.swf"
/>

These visualisations are cool as tasters for what might be, but they are "here's one we made earlier". Where are the tools to automate all this? I have no doubt such tools have been created in academic research projects, but let's see them in action. I'd love to see the source code hosts - sourceforge, google code, github, et al - integrate this technology to produce visualisations on the fly.