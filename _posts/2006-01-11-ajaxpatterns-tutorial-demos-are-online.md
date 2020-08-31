---
id: 257
title: 'AjaxPatterns Tutorial: Demos are Online'
date: 2006-01-11T04:09:05+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajaxpatterns-tutorial-demos-are-online
permalink: /ajaxpatterns-tutorial-demos-are-online/
dsq_thread_id:
  - "394414957"
  - "394414957"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Javascript
  - Links
  - Tutorial
---
<p>Here's a heads-up on the tutorial to be included with "Ajax Design Patterns". I'll let you know when the tutorial text is available, but for now, the demos are running:</p>

<p><a href="http://ajaxify.com/tutorial">Demos for the AjaxPatterns Tutorial</a></p>

<p>The first half is a fairly standard intro to Ajax, using the Foundational Technologies patterns (<a href="http://www.ajaxify.com/tutorial/display/">Display Manipulation</a>, <a href="http://www.ajaxify.com/tutorial/display/">Web Remoting</a>, <a href="http://www.ajaxify.com/tutorial/display/">Dynamic Behaviour</a>).</p>

<p>The second half is more interesting, as it documents the Ajaxification of Ajaxagram, an anagram finder (finds all combinations of a word, no dictionary used so as to keep the business logic simple). It begins as a <a href="http://www.ajaxify.com/tutorial/ajaxagram/">conventional web app</a> First, into <a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/">a basic Ajax version</a>. Then with a number of patterns progressively applied: first, <a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/">Live Search, Progress Indicator, and One-Second Spotlight (Yellow Fade Technique)</a> (about 3 lines, 8 lines, and 3 lines of code respectively). Followed by <a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/performant/">Submission Throttling</a>. And finally, I want to state loudly that most of the patterns don't have to be implemented by hand, thanks to the <a href="http://ajaxpatterns.org/Ajax_Frameworks">many great Ajax libraries and frameworks</a> available. For that reason, <a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/performant/library">the final refactoring</a> is not about one particular pattern, but is instead about introducing a library. In this case, the AjaxPatterns library.</p>

<a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/performant/library"><img src="http://img4.imageshack.us/img4/1760/ajaxagramfadein24ry.png"/></a>

<p>Following the Ajaxification, I'll give some suggestions for further enhancements and refactorings. Some people like to learn by hacking an existing app rather than building it from scratch. Taking the code base established in the final version of Ajaxagram, it should be easy to play around with many of the Ajax patterns. For example, use an <a href="http://ajaxpatterns.org/XML_Message">XML Message</a> instead of the custom-format <a href="http://ajaxpatterns.org/Plain-Text_Message">Plain-Text Message</a> that's used. Or try a different <a href="http://ajaxpatterns.org/One-Second_Spotlight">visual effect</a> in place of the Yellow-Fade Technique.</p> One thing you'll notice is there's only five characters due to the exponential nature of anagrams. A nice refactoring would be to use a <a href="http://ajaxpatterns.org/Virtual_Workspace">Virtual Workspace</a> so the anagrams are loaded gradually.