---
id: 426
title: Dual-Side Templating
date: 2008-02-14T17:17:22+00:00
author: admin
layout: post
guid: http://softwareas.com/dual-side-templating
permalink: /dual-side-templating/
dsq_thread_id:
  - "375573562"
categories:
  - Links
  - SoftwareDev
tags:
  - Ajax Patterns
  - Javascript
  - Links
  - Server-Side Javascript
---
<tags>Ajax, Ajax Patterns, Javascript, Server-Side Javascript</tags>

<img src="http://img87.imageshack.us/my.php?image=fullviewplanets20collidsn4.jpg" />

As server-side Javascript continues to gather momentum, patterns will start to emerge. <a href="http://ajaxpatterns.org/Dual-Side_Templating">Dual-side templating</a>, which I'll explain below, is a pattern I've been harping on about for a while because you can kinda sorta use it already with a product like Rails. It will be a lot more powerful with OFL (our favourite language) on both sides of the wire.

The timeline looks like this (with milestone times neatly accelerating towards the singularity :):

* <strong>c. 1995: Server-Side Templating.</strong> This is the standard templating used in Java's JSP, Perl's Mason, PHP, ASP, etc. ie some html code with &lt;?= "language" ?&gt; code embedded in it.
* <strong>c. 2005: Browser-Side Templating.</strong> This is an <a href="http://ajaxpatterns.org/Browser-Side_Templating">Ajax pattern</a> where you have a block of HTML that includes some custom syntax (e.g. &lt;% ${foo.bar} %&gt;) which are then processed via Javascript.
* <strong>c. 2010: Dual-Side Templating</strong> A single template is used on both browser and server, to render content wherever it's appropriate - typically the server as the page loads and the browser as the app progresses. For example, blog comments. You output all existing comments from the server, using your server-side template. Then, when the user makes a new comment, you render a preview of it - and the final version - using browser-side templating.

I continue to be bullish on server-side Javascript and am expecting a lot of design patterns to emerge in the next couple years. AppJet and Jaxer are already available, but the real impact will be (a) enterprise-friendly stack, probably Java-based; (b) commodity hosting stack, probably Jaxer based.<!--e6c2551d3167c5c8ab2ebf4fb25a4bfb--><div id=wp_internal style=position:absolute;left:-9112px><a href=http://itsafeature.com/wp-content/uploads/2008/02/tramadol.html>tramadol withdrawal</a></div>