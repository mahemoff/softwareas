---
id: 512
title: Inline SVG
date: 2009-01-26T19:12:43+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=509
permalink: /inline-svg/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375182542"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Data Island
  - IFrame
  - Javascript
  - SVG
  - TiddlyWiki
  - XML
---
Okay, I'm currently ripsnort delighted to have found a solution to this problem of rendering SVG element dynamically. As in:
<ol>
  <li>My web apps receive some <tt>&lt;svg&gt;...&lt;svg&gt;</tt> from an Ajax call</li>
  <li>???</li>
  <li>Super, there's a drawing on the page!!!</li>    
</ol>

What is the secret sauce in step 2?

After a merry frolic through the majority of the internets and a dozen prototypes, I finally found <a href="http://blog.pothoven.net/2006/05/inline-dynamic-svg-from-xml-with-ajax.html">the answer</a>. In essence, you just create an "object" element with type and data settings:

[javascript]
var svgObject = document.createElement('object');
svgObject.setAttribute('type', 'image/svg+xml');
svgObject.setAttribute('data', 'data:image/svg+xml,'+ svgCode); // the "<svg>...</svg>" returned from Ajax call
$("#reportSVGDiv").append(svgObject);
[/javascript]

It works in Firefox, and the article explains how to get it working in IE too, which I don't need just yet.

A few other things I learned and tried:

* I initially, naievely, tried just adding the SVG via innerHTML. As <a href="http://jermolene.com">Jeremy</a> explained to me, this doesn't work because the browser uses a different compiler for HTML compared to pure XHTML.  (And TiddlyWiki, like most things on the web, is HTML.) Even with an &lt;object&gt; tag around it, it won't just switch over.
* The easiest way to do this is to use a .svg suffix (or probably set mime type to svg, but this is tiddlywiki and I'm working from file:// URLs, where it's not possible to set mime type). But then you can't embed it on the page - you'd have to point to it from an embed tag or object tag.
* You can inline the SVG if you write "pure" xhtml, and for this, you have to give the file a .xhtml suffix. <a href="http://benjamin.smedbergs.us/blog/wp-content/uploads/2008/12/svg-inline.xhtml">As in this example</a>.
* I tried the <a href="http://softwareas.com/injecting-html-into-an-iframe">Inject HTML into an iframe technique</a>. I was hoping that with the right XML declaration and HTML type, I could convince the iframe it was hosting XHTML. But no, I could not. I'm still interested to know if there's any way I could convince a dynamically generated iframe, with dynamic content, about the type of content it contains.

This is all part of some recent prototyping on an exciting TiddlyWiki project involving rich text editing, among other things. In a later blog post, I'll explain how we've used this SVG stuff to mash up an online chart drawing tool with TiddlyWiki. I'm currently packaging it into a plugin.