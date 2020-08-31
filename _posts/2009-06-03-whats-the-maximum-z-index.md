---
id: 543
title: 'What&#8217;s the Maximum Z-Index?'
date: 2009-06-03T22:46:55+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=540
permalink: /whats-the-maximum-z-index/
dsq_thread_id:
  - "375144881"
categories:
  - SoftwareDev
tags:
  - Ajax
  - CSS
  - HTML
  - Z-Index
---
<a href="http://twitter.com/mahemoff/status/2020459916"><img style="width:400px" src="http://img.skitch.com/20090603-nea4qqrijh9hmy8yck3pbc5f6n.jpg"></a>

Z-index is the CSS property governing how high in the stack an element is, if you visualise the elements as appearing in a 3D stack coming out of the page. The actual value of an element's z-index doesn't matter; just its value relative to other elements on the page. Elements with higher z-indexes appear on top of elements of lower z-indexes.

I was just designing a bookmark for Scrumptious (a TiddlyWeb powered tool to have discussions around websites; I'll talk about it in a future article). And with a bookmarklet, I need it to appear above everything else on the page. So it needs a higher z-index than everything else. Maybe not the highest z-index possible, since there might be apps that need to sit above my app's bookmarklet (Design For Extensibility). But I still need to know the maximum z-index.

It would be nice if the standards publshed the maximum allowed z-index. Every reference always makes a comment like "there's no real limit". For good reason too, since the W3C standards don't really cover this. <a href="http://www.w3.org/TR/CSS2">The CSS Spec (2.1)</a> goes so far as to include an <a href="http://www.w3.org/TR/CSS2/zindex.html">"Elaborate description of Stacking Contexts"</a>, and it's even called "zindex.html", but even here, omits to pin down the max z-index value.

<a href="http://stackoverflow.com/questions/491052/mininum-and-maximum-value-of-z-index">A handy summary was stated on StackOverflow</a> (which has fast become the central resource for programming FAQs and a site I have quickly come to adore for its clear mission, clean design, and community feel):

<blockquote>
<p>
So basically there are no limitations for z-index value in the CSS standard, but I guess most browsers limit it to signed 32-bit values (âˆ’2147483648 to +2147483647) in practice (64 would be a little off the top, and it doesn't make sense to use anything less than 32 bits these days)
</p>
</blockquote>

Looking further, I came across <a href="http://www.puidokas.com/max-z-index/">the most comprehensive summary of the situation</a>, published recently. It also highlights the fact that it's not just the maximum value we want, but what happens if we exceed it.

<blockquote>
<p>I made a <a href="http://puidokas.com/examples/z-index_max/">simple test page</a> to find these limits and figure out what happens when you exceed them.</p>

<style type="text/css">
    #z-index-table      { width:585px; padding-bottom:10px; }
    #z-index-table th   { background:#ddd; font-weight:bold; font-size:93%; padding:5px; }
    #z-index-table td   { padding:5px; border-bottom:1px solid #6cf; }
</style>
<table style="width:400px;">
<tr>
<th>Browser</th>
<th>Max z-index value</th>
<th>When exceeded, value changes to:</th>
</tr>
<tr>
<td>Internet Explorer 6</td>
<td>2147483647</td>
<td>2147483647</td>

</tr>
<tr>
<td>Internet Explorer 7</td>
<td>2147483647</td>
<td>2147483647</td>
</tr>
<tr>
<td>Internet Explorer 8</td>
<td>2147483647</td>
<td>2147483647</td>
</tr>

<tr>
<td>Firefox 2</td>
<td>2147483647</td>
<td>*element disappears*</td>
</tr>
<tr>
<td>Firefox 3</td>
<td>2147483647</td>
<td>0</td>
</tr>
<tr>

<td>Safari 3</td>
<td>16777271</td>
<td>16777271</td>
</tr>
<tr>
<td>Safari 4</td>
<td>2147483647</td>
<td>2147483647</td>
</tr>
<tr>
<td>Opera 9</td>

<td>2147483647</td>
<td>2147483647</td>
</tr>
</table>
</blockquote>

So the best way would be to use browser detection and pick the max from there. But if not, use 2147483647.