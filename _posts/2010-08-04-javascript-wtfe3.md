---
id: 931
title: Javascript WTFe3
date: 2010-08-04T22:16:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=931
permalink: /javascript-wtfe3/
dsq_thread_id:
  - "375574752"
categories:
  - SoftwareDev
tags:
  - Javascript
  - wtfjs
---
<pre>
&gt; parseInt(1000)
1000
&gt; parseInt(1000.0)
1000
&gt; parseInt("1000.0")
1000
&gt; parseInt(1e3)
1000
&gt; parseInt("1e3")
1
</pre>

<p><a href="http://wtfjs.com/">WTFJS</a></p>

So how to actually parse it with Javascript built-in? Spoiler alert - select the following white text:

 ----------------
<span style="color:white">parseInt(parseFloat("1e3"))</span>
 ----------------
(Thanks @CAIndy)