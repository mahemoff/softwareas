---
id: 495
title: Man pages that read more like legal contracts
date: 2008-11-17T19:47:23+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=492
permalink: /man-pages-that-read-more-like-legal-contracts/
dsq_thread_id:
  - "447503026"
categories:
  - SoftwareDev
tags:
  - Documentation
  - Man Pages
  - Unix
---
Case in point: I want to use "find" to find files I've recently created.

<a href="http://www.gsp.com/cgi-bin/man.cgi?section=1&topic=find"><tt>man find</tt> (BSD edition)</a>:

<blockquote>
     -ctime n[smhdw]
             If no units are specified, this primary evaluates to true if the difference between the time of
             last modification time and the time find was started, rounded up to the next
             full 24-hour period, is n 24-hour periods.
<br/> <br/>
             If units are specified, this primary evaluates to true if the difference between the time of
             last modification time and the time find was started is exactly n units.
             Please refer to the -atime primary description for information on supported time units.
</blockquote>

Humane documentation FAIL! The precision here is all well and good to include somewhere, but unnecessary for most usages. Please, just tell me what I need to know and <a href="http://www.amazon.com/exec/obidos/ASIN/0321344758">Don't Make Me Think!</a>.

What I wanted to see:

<hr>
-mtime t

Include only files modified t days ago. You will typically want to specify a +/- sign. e.g. "-ctime +3" for files created 3 or more days ago. To measure in another unit of time, you can append one of the following to t: s for seconds, m for minutes, h for hours, d for days, w for weeks, <strong>but note that "-ctime" unfortunately only works if the time is at least one day</strong>. For example, "find . -ctime 1d6h" will return files created in the past 30 seconds. 

Technical detail: (the legalese stuff goes here. 99% of users will never need it and never read it.)
<hr>

The improved version focuses on what the typical user needs to know, uses active voice, avoids the cross-reference (it's documentation, not code, so embrace redundancy!), and most importantly, includes <a href="http://softwareas.com/documentation-needs-examples-duh">an example</a>. (The man page does include examples at the bottom, but (a) they should be included against each component too; and (b) they still shy away from concrete values: "-newer ttt"!!!)

A lot of these man pages have been around for two decades or more, with minimal changes to my knowledge; I'd love to see someone like Ubuntu sponsor an effort to bring them up to date. <a href="http://confusedofcalcutta.com/2008/11/11/faster-horses-in-the-age-of-co-creation/">Plain English without dumbing down</a>.

<a href="http://www.flickr.com/photos/sfjase/2255340060/"><img src="http://picupper.com/2008/11/17/parkingsign.jpg" style="width:200px;"/></a>
