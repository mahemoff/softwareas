---
id: 297
title: 134 Ajax Frameworks and Counting
date: 2006-05-10T10:05:59+00:00
author: admin
layout: post
guid: http://www.softwareas.com/134-ajax-frameworks-and-counting
permalink: /134-ajax-frameworks-and-counting/
dsq_thread_id:
  - "375572869"
categories:
  - SoftwareDev
tags:
  - Ajax Experience
  - AjaxPatterns
  - Frameworks
  - Libraries
  - Links
  - Patterns
---
I'm here in SF for <a href="http://theajaxexperience.com">The Ajax Experience</a>, talking about <a href="http://theajaxexperience.com/speaker_topic_view.jsp?topicId=274">design principles and patterns for Ajax</a> (big surprise!), and one of the things my presentation will point out is the importance of libraries and frameworks in implementing Ajax patterns. Ahead of the talk, I just did a quick count of <a href="http://ajaxpatterns.org/Ajax_Frameworks">frameworks and libraries on the wiki</a>. Turns out there are <b>58 in pure Javascript and another 76 with back-end support in PHP, Java, or whatever.</b> This includes <a href="http://ajaxpatterns.org/DotNet_Ajax_Frameworks">13 for .Net</a>, and no less than 22 for each of <a href="http://ajaxpatterns.org/PHP_Ajax_Frameworks">PHP</a> and <a href="http://ajaxpatterns.org/Java_Ajax_Frameworks">Java</a>.

Overall, that's <b>134 Ajax frameworks and libraries out there</b>, many of them under a year old! It's true that a few of the pure Javascript libraries are things like Drag-And-Drop that have been around a few years, but only a few of those. The rest are <a href="http://ajaxpatterns.org/Javascript_Multipurpose_Frameworks">all-encompassing</a>, like Dojo, or related to <a href="http://ajaxpatterns.org/Javascript_Remoting_Frameworks">remoting</a>, like ACE, or related to XML and DOM manipulation in a manner closely associated with Ajax, like logging and effects libraries.

When I transcribed the frameworks to form an appendix for <a href="http://ajaxpatterns.org">the book</a>, there were about 90 patterns. That was in December. So roughly 45 new frameworks since then, about one every three days. Nice going! Stuff like this makes life a *lot* easier for developers, no matter what they're approach to Ajax architecture. Even if a developer doesn't want to go near Javascript with a ten-foot pole, they're still going to reap the benefits from a server-side framework (Rails etc). Furthermore, the server-side framework is going to reap the benefits of all these pure Javascript libraries - a number of server-side frameworks make use of Dojo, Scriptaculous, and Mochikit.

<b>Patterns and frameworks go hand in hand. It's not that a framework "makes patterns", as some sales reps like to imply, but frameworks do support particular patterns.</b> Most GUI toolkits, for example, are based closely on the Observer pattern. Java's IO library is based on Decorator. In the case of Ajax, there are libraries like Scriptaculous which map closely to particular patterns, like <a href="http://ajaxpatterns.org/One-Second_Spotlight">One-Second Spotlight</a>. The best reference on this stuff is Ralph Johnson's visionary 1997 paper, <a href="http://www.idi.ntnu.no/grupper/su/courses/dif8901/papers2003/P-r22-johnson97.pdf">Frameworks = Components + Patterns</a> (Comms of the ACM, October, 1997).