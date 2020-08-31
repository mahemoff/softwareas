---
id: 424
title: BlingText and Banner
date: 2008-02-12T23:51:36+00:00
author: admin
layout: post
guid: http://softwareas.com/blingtext-and-banner
permalink: /blingtext-and-banner/
dsq_thread_id:
  - "389128241"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Links
---
<tags>Ajax, AjaxPatterns</tags>

As <a href="http://explore.twitter.com/mahemoff/statuses/675805672">foretweeted last week</a>, I created a little Ajax app called <a href="http://ajaxify.com/run/blingtext">BlingText</a>.

<a href="http://ajaxify.com/run/blingtext"><img style="width: 400px; height: 200px;" src="http://img528.imageshack.us/img528/7329/blingtextqh1.png" /></a>

As you can see, it takes a message and provides some ASCII renderings. In particular, it includes a port of the old UNIX/C <a href="http://en.wikipedia.org/wiki/Banner_(Unix)">Banner</a> <a href="http://unix-tree.huihoo.org/MiniUnix/usr/source/s1/banner.c.html">utility</a>.

If I do more work on it, the main improvements will be:
<ul>
  <li><strong>Options.</strong> Let the user specify, for each transformation, parameters such as the fill character ("*") and amount of spacing.</li>
  <li><strong>Better OO (internal change).</strong> Each of the transformations is at present a terse strategy object, which is good. However, there's no inheritance going on, so it could be better.</li>
</ul>