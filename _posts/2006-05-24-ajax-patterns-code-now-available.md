---
id: 301
title: Ajax Patterns Code Now Available
date: 2006-05-24T15:33:06+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-patterns-code-now-available
permalink: /ajax-patterns-code-now-available/
dsq_thread_id:
  - "394925402"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Demos
  - Links
  - PHP
---
<strong>All code for <a href="http://ajaxify.com/run/">the Ajax Patterns demos</a> is now available.</strong> This is the code used as <a href="http://ajaxify.com/run/">examples for many of the patterns</a> at <a href="http://ajaxpatterns.org">AjaxPatterns.org</a>, as well as the <a href="http://ajaxify.com/tutorial/">Pattern-Led Tutorial</a> that forms Chapter 2 of the "Ajax Design Patterns" book to be published next month.

<a href="http://ajaxify.com/ajaxdemos.zip">Download the code - ajaxdemos.zip</a>.

<a href="http://ajaxify.com/INSTALL.txt">Read the installation notes</a>. Basically, you need PHP and Apache, and optionally MySQL is required for the wiki demos. The install should be pretty basic, as the notes indicate:

<pre>
* Unzip the package to a temporary location and copy
  run/, tutorial/, and records/ to the apache document root.
  Assuming the doc root is /apache/document/root:

    cp run tutorial records /apache/document/root.

  (Alternatively, if you have sufficient access, set up a new
   virtual host in apache's httpd.conf and point it to the root
   of the unzipped directory, ajaxdemos/).

* Ensure the server can write to (the initially empty) records/
   directory. The easiest (though not the most secure) way is:

    chmod 777 apache/document/root/records

* Open up run/.htaccess and follow instructions there to set
   the library path.

* Finished!
</pre>

You might wonder why the server-side uses PHP, when I'm more of a Java+Ruby kind of guy.  Realistically, the choice was Java versus PHP due to popularity. PHP was chosen because the code needs to be easy to install, and LAMP is a lot more ubiquitous and easier to work with than integrating Java+Tomcat+MySQL together. I understand Java is at least shipping with Debian at some point, but right now, there's few things easier than getting a LAMP setup running, especially with all the one-click installers around (http://www.apachefriends.org/en/xampp.html).

From a development perspective, I also found PHP more productive for the experimental style of development that went into the Ajax demos. The usual drivers for Java - maintainability, security, etc. - weren't a factor. PHP also has the sort-of-merit of being the Switzerland of server-side languages. Use Perl, Java, C#, or Rails, and you're going to be flamed loudly from some contingent. But use PHP and most non-PHP coders will say something about it would have been nice if you'd used Java/etc but I can see your point and shrug their shoulders a bit. As it happens, only a few patterns (need to) delve into server-side details, so the only real impact of using PHP is if people want to hack the code or look further into the details of implementing a pattern.

<a href="http://ajaxify.com/run/assistiveSearch/"><img src="http://img513.imageshack.us/img513/3884/assistive8jo.png"/></a>