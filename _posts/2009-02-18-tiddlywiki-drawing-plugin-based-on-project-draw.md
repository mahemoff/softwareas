---
id: 525
title: TiddlyWiki Drawing Plugin based on Project Draw
date: 2009-02-18T10:49:21+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=522
permalink: /tiddlywiki-drawing-plugin-based-on-project-draw/
dsq_thread_id:
  - "375574169"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Drawing
  - Javascript
  - Osmosoft
  - Plugin
  - Project
  - Project Draw
  - TiddlyWiki
---
I've been creating <a href="http://tiddlywiki.mahemoff.com/DrawingPlugin.html">a drawing plugin for TiddlyWiki</a> (<a href="http://trac.tiddlywiki.org/browser/Trunk/contributors/MichaelMahemoff/plugins/DrawingPlugin/DrawingPlugin.js">SVN trunk</a>). It delegates the actual drawing editing to Project Draw (<a href="http://draw.labs.autodesk.com/ADDraw/documentation/topic/com.autodeskdraw.help/docs/help/user_home.html">docs</a>; <a href="http://draw.labs.autodesk.com">demo</a>), a browser-based drawing editor from <a href="http://labs.autodesk.com/">Autodesk Labs</a>.

Here's a screencast:

<object width="400" height="300"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=3265891&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=3265891&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><br /><a href="http://vimeo.com/3265891">TiddlyWiki Drawing Plugin based on Project Draw</a> from <a href="http://vimeo.com/user960717">Michael Mahemoff</a> on <a href="http://vimeo.com">Vimeo</a>.

Autodesk Labs' Project Draw editor looks like this:

<img src="http://img.skitch.com/20090218-89wkt8qwf7mx9arffhxyiqni7.jpg" style="width:380px;" />

... and the tool has a nice set of RESTful services we can make use of:

<img src="http://img.skitch.com/20090218-dsxqdji76f79kqwr266gj8pxce.jpg" style="width:380px;" />

Project Draw doesn't have any specialised cross-domain API, e.g. using JSON or OAuth,  so normally you would have to proxy any calls via the server. However, a standard TiddlyWiki runs against a file:// URL and can therefore bypass cross-domain restrictions; hence, it was possible to build this plugin using the same kind of XMLHttpRequest calls as Project Draw does for its own <a href="http://draw.labs.autodesk.com/ADDraw/apitester.html">RESTful services demo</a>.

One likely use of Project Draw is in conjunction with <a href="simonmcmanus.wordpress.com/2008/08/11/offline-is-back-online/ ">TiddlyDocs</a>, which will generally run as a standard website - off a http:// URL. Hence, we will need to do some proxying in order to get around cross-domain restrictions.

Also, the tool isn't fully working in IE yet; I'm working on that.

You create a new drawing with the New Drawing menu item. This is simply a &lt;&lt;newDrawing&gt;&gt; macro and could appear anywhere in the page.

<img src="http://img.skitch.com/20090218-ent9dd6rnqa8q5627f994tunx3.jpg" style="width:380px;" />

And you can set image dimensions in edit mode:

<img src="http://img.skitch.com/20090218-8uyccripgh17616im7gipy4fm5.jpg" style="width:380px;" />

... which will cause images to be clipped depending on the dimensions:

<img src="http://img.skitch.com/20090218-n81aec3ptmgqrw8m5xhuhey64c.jpg" style="width:380px; " />

By default, images are rendered as SVG, using <a href="softwareas.com/inline-svg">the tricks I discussed earlier for inline SVG</a>. However, this is only supported for non-IE browsers, or IE with Flash-based SVG support. I am still working on IE support. Without SVG, the image will fall back to a bitmap image (fortunately, Project Draw can output an image as SVG or bitmap). However, note that the bitmap image always shows the whole thing; so rather than being clipped, it will re-scale, which could lead to a lot of whitespace being shown in TiddlyWiki. For this reason, in Project Draw, you should set the page dimensions to avoid any whitespace:

<img src="http://img.skitch.com/20090218-xi58jq5gqc48j8xbxqmrwb31b8.jpg" style="width:380px; " />