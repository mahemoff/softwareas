---
id: 176
title: 'Ajax Frameworks &#8211; JS, Server-Side, or Both'
date: 2005-08-13T17:58:01+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-frameworks-js-server-side-or-both
permalink: /ajax-frameworks-js-server-side-or-both/
tags:
  - Framework
  - Javascript
  - Links
  - Software
  - Taglibs
dsq_thread_id:
  - "391793224"
  - "391793224"
categories:
  - SoftwareDev
---
[Jason Salas](http://weblogs.asp.net/jasonsalas/) is a blogger-podcaster who's been writing a lot of good stuff about Ajax lately. He notes the new [ComfortASP .Net](http://www.daniel-zeiss.de/ComfortASP/) abstracts away the DHTML/JS so you can do everything server-side. The new [Ajax JSP Taglib](http://ajaxtags.sourceforge.net/) does that too. The idea's been used previously with libraries like the struts validation module. Custom libraries are also useful - in the past I've hand-coded JSP taglibs to provide better user feedback in the browser, but prevent Java programmers from having to deal with the JS.

**So of the [Ajax Frameworks](http://ajaxpatterns.org/Ajax_Frameworks) out there, there's a fairly common theme: either libraries let you code *everything* in Java/.Net/etc, or they are pure DHTML/JS or sometimes both.**

Two reactions:
<ul>
<li><b>In aggressive dotcom markets, the pure abstraction libraries won't work. In mainstream intranet apps, they will be a big thing.</b>

There are already a lot of smart JS developers and many more coming on. Where Ruby is riding the Rails train, JS is surfing the Ajax wave (I know JS and Ajax are essentially the same technology, but it sounded cool. More accurately, JS is benefiting from the Ajax branding.) So you have the <a href="http://www.openjsan.org/">new JSAN project</a>, all the stuff coming out of Scriptaculous and DOJO and Rico. And then you have talented guys like Jon Tiersen applying their Java/Agile expertise to <a href="http://mir.aculo.us/articles/2005/07/28/automatic-testing-of-your-web-pages-with-javascript">improve JS tooling</a>. So overall, you will be able to do a lot more with JS than pure abstraction. Market forces dictate that public dotcoms will be forced to work directly on the browser-side in order to keep their edge.


However, in the other <a href="http://www.joelonsoftware.com/articles/FiveWorlds.html">world</a> of internal projects, where satisficing - doing enough to just get by - is the logical mode of development, these libraries will be superb. For typical intranet apps, the incremental benefit of hand-coding JS often isn't there - there's not enough users and it's often more cost-effective to train users to work around problems. Very   different story from dotcoms.

<li> <b>I'd like to see these pure server-side libraries offer some pluggable behaviour, to let users customise lots of browser-side appearance and behaviour if they want to</b>. Provide sensible defaults so users can write pure server-side code, but let them tweak it later on.  So, in the browser-side, you should be able to plug in new appearances, new event handlers, maybe even event interceptors. I understand <a href="http://www.nakedobjects.org/">Naked Objects</a> is headed in that direction - it will autogenerate all GUI code from the domain model, but you can then hand-code a particular object's look-and-feel if so desired. To me, that's the key to a good framework: strong flexibility (but only where it matters), combined with sensible defaults.</li>
</li></ul><!--13c1a54d8b85e2f95ab7237461785ea4-->