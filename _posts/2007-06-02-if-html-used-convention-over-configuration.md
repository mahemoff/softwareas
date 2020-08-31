---
id: 381
title: 'If HTML Used Convention Over Configuration &#8230;'
date: 2007-06-02T10:17:54+00:00
author: admin
layout: post
guid: http://www.softwareas.com/if-html-used-convention-over-configuration
permalink: /if-html-used-convention-over-configuration/
dsq_thread_id:
  - "375573307"
categories:
  - Links
  - SoftwareDev
tags:
  - Abundance Thinking
  - Convention Over Configuration
  - HTML
  - Javascript
  - Links
  - Rails
---
Browsers would automatically pull in CSS and JS according to the filename and I would no longer have to look for an example every time I need a link or script tag.

In the absence of any other spec, /abc/def.html would cause the browser to look for /abc/def.css and /abc/site.css and /site.css. And then it would look for the same, but in JS - /abc/def.js, /abc/site.js, and /site.js. If I had all the time in the world, I'd make an Apache filter to do just that.

This would slow things down a little, but have you noticed - the world is becoming faster? It's an another example of abundance thinking. Also, if it was a standard, it would not really slow things down as browsers and servers would develop protocols for speeding things up.

So I created a little <a href="http://ajaxpatterns.org/Ajax_Template">Ajax web app template</a> to put all the skeleton Ajax code on one page.

<h2>HTML</h2>
<pre>
&lt;html&gt;
  &lt;head&gt;
     &lt;title&gt;Hello World!&lt;/title&gt;

     &lt;script type=&quot;text/javascript&quot; src=&quot;app.js&quot;&gt;&lt;/script&gt;
     &lt;link rel=&quot;stylesheet&quot; type=&quot;text/css&quot; href=&quot;app.css&quot;/&gt;

  &lt;/head&gt;
  &lt;body&gt;
      &lt;h1&gt;Hello World!&lt;/h1&gt;
      &lt;input id=&quot;search&quot; name=&quot;search&quot; /&gt;

  &lt;/body&gt;
&lt;/html&gt;
</pre>
<h2> CSS </h2>
<pre>
body { background-color: white; }
div.error { font-color: red; }
#search { width: 200px; }
</pre>
<h2> Javascript </h2>

<pre>
function $(id) { return document.getElementById(id); }

window.onload = function() {
  $(&quot;search&quot;).onclick = function() { alert(&quot;The search begins!&quot;); }
}
</pre>