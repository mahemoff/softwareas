---
id: 378
title: 'Announcing Bitjuice: Ajax Bitmap API'
date: 2007-05-27T19:55:22+00:00
author: admin
layout: post
guid: http://www.softwareas.com/announcing-bitjuice-ajax-bitmap-api
permalink: /announcing-bitjuice-ajax-bitmap-api/
dsq_thread_id:
  - "375573299"
categories:
  - Links
  - SoftwareDev
tags:
  - Bitjuice
  - DHTML
  - Graphics
  - Javascript
  - Links
---
<!--more--><a href="http://ajaxpatterns.org/bitjuice"><img src="http://ajaxian.com/wp-content/images/bitjuice.png" width="320" height="240"></a>

<a href="http://ajaxpatterns.org/bitjuice">Bitjuice</a> is a little library I made to do bitmap/raster graphics in the browser. The aim is to make it easy to write <a href="http://softwareas.com/ajaxjavascript-8-ways-to-create-graphics-on-the-fly">"Ajax graphics"</a> - graphics you can update real-time in the browser. And at the same time, maintain compatibility with all major browsers and old browsers too. That's why it doesn't use any new-fangled SVG/Canvas APIs. Just a plain-old HTML table, where we manipulate the CSS cell background style.

Here's an interactive <a href="http://ajaxify.com/run/bitjuice/form/scratchpad">Scratchpad</a>, where you can play around with programming against the API. I think it's neat that Ajax lets us make it this easy to get your hands dirty with a new API - no download, no install, no fuss!

<a href="http://ajaxify.com/run/bitjuice/form/scratchpad"><img src="http://img178.imageshack.us/img178/1467/bitrxk2.png"></a>

How to use it? The API is like any typical drawing-on-a-canvas-type APi you've ever used.

<pre>
 *** BASIC USAGE ***
 var bitmap = new Bitmap(10,20); // width, height
 containerElement.appendChild(bitmap);
 bitmap.drawPoint(5,5,"pink"); // x,y,html colour

 *** ADVANCED USAGE ***
 var bitmap = new Bitmap(10,20, {container:containerElement, blankColor:"gray"});
 bitmap.drawLine(1,2,5,5,"pink");
 bitmap.drawRect(1,2,5,5,"pink");
 bitmap.drawFilledRect(1,2,5,5,"pink");
 bitmap.destroy(); // Same as containerElement.removeChild(bitmap);
</pre>

There's various work to be done, mainly in optimising performance because I would like to make it possible to plot fairly quickly.

I can envision a a number of potential uses. Interactive bitmap editor, tool for learning Javascript or programming in general (the scratchpad), simulations such as Game Of Life (which I really want to implement), mathematical graphing, process monitoring. 

It's licensed under the liberal, non-viral, MIT License. Ships as <a href="http://ajaxify.com/run/bitjuice/dist">a single JS file</a>.