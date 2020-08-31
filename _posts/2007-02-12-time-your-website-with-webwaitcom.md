---
id: 364
title: Time Your Website with WebWait.com
date: 2007-02-12T05:39:47+00:00
author: admin
layout: post
guid: http://www.softwareas.com/time-your-website-with-webwaitcom
permalink: /time-your-website-with-webwaitcom/
dsq_thread_id:
  - "375573221"
categories:
  - SoftwareDev
tags:
  - Benchmark
  - IFrame
  - Javascript
  - Links
  - Performance
  - WebWait
---
<a href="http://webwait.com"><img style="text-align: center;" src="http://webwait.com/images/webwait.jpg"/></a><br/>

<em><b>Update (2 days later):</b> The siteâ€™s been popular - 10k+ views yesterday. Hit Delicious Popular and somehow got caught up in the German blogosphere, the greatest source of hits. Technorati it. Thereâ€™s a good discussion in Ajaxian of the strengths and weaknesses of this technique. As with AjaxPatterns, which also reached Delicious Popular, it failed to attract Digg users somehow. (Digg was supposedly inspired by Delicious Popular. Incidentally, Digg doesn't let you submit URLs with fragment identifiers such as http://webwait.com#digg.com, which rules out any Ajax site attempting to allow bookmarks.) Go figure. Or better, <a href="http://digg.com/tech_news/How_long_does_the_Digg_homepage_take_to_fully_load">go Digg</a> :).</em>

<p>Here's another new website - <a href="http://webwait.com">WebWait</a>. I wanted a portable, consistent, way to
benchmark Ajax web apps, that would show how long the wait is (though it's useful for any app, especially if there were a lot of images, for instance). Using a 
command-line tool like curl is an improper simulation and doesn't cut it as a 
proper simulation. WebWait has the following benefits:</p>
<ul>
  <li>Runs in a browser. You get actual load times in the same client web users 
  are running, not simulated times.</li>
  <li>Runs in multiple browsers. There are plugins that do this, but as well as  
  the installation overhead, they are usually specific to one browser. With 
  WebWait, you can just cut-and-paste the same URL into different browsers. (No 
  Safari yet as it doesn't listen to iframe onload ???.)</li>
  <li>Respects your cookies and authentication - If you can access a URL in a web
  page, you can benchmark it with WebWait. Trying to set up cookies for use 
  with a command-line tool like Curl is hard work. Doing it with a plugin is 
  usually impossible. Doing it with a third-party website is dangerously 
  insecure.</li>
</ul>
<p><img width="380" height="200" style="text-align: center;" src="http://img368.imageshack.us/img368/862/webwaitlq6.png"></p>
<p>Quick feature list as it stands right now:</p>
<ul>
  <li>Basic functionality: Type a URL, see how long it takes to load.</li>
  <li>Option: Set the delay between calls. WebWait will call the website
  multiple times and provide an average load time.</li>
  <li>Option: Set the number of calls before ceasing activity.</li>
  <li>Ability to pause.</li>
  <li>Partially transparent lightbox eye candy.</li>
  <li><a href="http://ajaxpatterns.org/Unique_URLs">Unique URLs</a> - it's
  Ajax, but that shouldn't stop you from bookmarking and sending URLs with
  details of the website being tested. Incidentally, implementing this rare but
  highly useful feature took three lines of Javascript.</li>
</ul>

<p>Have fun. Any comments/suggestions, please let me know!</p>

<p>See the <a href="http://webwait.com/faq.html">FAQ</a> for more info.</p>
