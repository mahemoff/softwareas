---
id: 528
title: 'TiddlyDocsDocs &#8211; Design Docs for Tiddly*'
date: 2009-03-26T14:00:41+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=525
permalink: /tiddlydocsdocs-design-docs-for-tiddly/
dsq_thread_id:
  - "389098057"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - Osmosoft
  - TiddlyDocs
  - tiddlyweb
  - TiddlyWiki
---
<img style="width:400px;" src="http://img.skitch.com/20090326-b4amdegnjs5aq8xdgjxcjdqeqd.jpg" alt="TiddlyDocs - document collaboration by divide and conquer - FireMoff (-;"/>

Since we're planning to use <a href="http://tiddlydocs.com">TiddlyDocs</a> internally, we're in need of some high-level documentation for TiddlyDocs in order to have it approved for certain uses.

My starting point was to locate, solicit, or produce documentation for TiddlyWiki and TiddlyWeb, the technologies on which TiddlyDocs is based.

For TiddlyWiki, useful sources are:
<ul>
	<li><a href="http://osmosoft.com/~psd/TiddlyWikiDeviceAccess/">Position Paper </a> Although it's technically a position paper for an event on device access, Paul Downey has done a great job of overviewing TiddlyWiki from both a high-level and technical perspective.</li>
	<li><a href="http://softwareas.com/tiddlywiki-internals-1-of-3-architectural-concepts">TiddlyWiki Internals Series</a> I wrote this when I joined Osmosoft, so a caveat is that  my knowledge of TiddlyWiki was at the time limited. OTOH it's the only detailed dive of the internals I'm aware of.</li>
	<li><a href="http://tiddlywiki.org/wiki/Main_Page">Community Wiki</a> Scouring around the official community wiki is another way to find a lot of useful info, particularly about the API.</li>
</ul>

For TiddlyWeb, there are less third-party sources, but fortunately its creator <a href="http://peermore.com">Chris Dent</a> puts a lot of effort into writing detailed notes. These are notes shipped with the code itself, notes on <a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers.wiki">the TiddlyWeb wiki</a>, and even some very useful notes in commit messages. Most recently, Chris has been producing some excellent doco at <a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers.wiki#[[Theory%20of%20Operation]]">here, inside the wiki</a>.

For TiddlyDocs, Simon has produced a nice new <a href="http://vimeo.com/3718346">screencast on TiddlyDocs</a> with animations. Video quality needs some polishing,  which we'll do in later versions, but he's done a great job motivating the product:

<object width="400" height="300"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=3718346&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=3718346&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><br /><a href="http://vimeo.com/3718346">TiddlyDocs Intro</a> from <a href="http://vimeo.com/user1447187">Simon McManus</a> on <a href="http://vimeo.com">Vimeo</a>.