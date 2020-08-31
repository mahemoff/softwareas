---
id: 349
title: XML Descriptors, Be Gone!
date: 2006-10-04T22:27:06+00:00
author: admin
layout: post
guid: http://www.softwareas.com/xml-descriptors-be-gone
permalink: /xml-descriptors-be-gone/
dsq_thread_id:
  - "375573130"
categories:
  - SoftwareDev
tags:
  - Agile
  - Configuration
  - EJB
  - XML
---
Dion posted a story about <a href="http://ajaxian.com/archives/widsets-nokia-mobile-widgets">Nokia's new mobile widgets</a>. This will be very cool if it's as good as it sounds. However, what got me was the XML-based config - three separate files for config, skin, and widgets. The widget config:

[xml]
<widget name="Example widget" version="0.1">

  <info>
    <creator>
      <user>username</user>
      <date>7.6.2006 12:00</date>
    </creator>

  <!-- Configuration of servicehandlers which the widget needs to operate -->
  <services>
    <service type="syndication" id="feed1">
	  <reference from="feedurlrss" to="feedurl"/>
	</service>
  </services>
[/xml]

My comment here isn't specifically about this project, because most APIs continue to use this convention. I don't get why APIs continue to come out requiring complex EJB-style XML config, in three different files no less. Learn from Rails and Pico and use code for config.

The arguments for XML config are fundamentally flawed:

<ul>
<li>"Anyone can edit it, not just programmers". And if you believe that, you're still waiting for your manager to learn FORTRAN and COBOL, thus rendering programmers obsolete. Mwuhahah. Obselete, I'll tells ya.</li>
<li>"It can be changed at runtime, no compilation required." This might occasionally be useful if the app's shipped off to another site, but that's a slim minority - it will either be a hosted app which you can easily re-deploy after re-compiling (as with these widgets) or a desktop app which will hopefully offer a nice config UI rather than requiring the user to hack some XML files! We like to develop standards to serve the vast majority, not the slim minority.</li>
<li>"It's neater." In any modern language, you can easily develop an API that lets you perform configuration with a grammar resembling a domain-specific language. I don't consider the above XML to be particularly neat, nor most EJB descriptors I've come across.</li>
<li>"It can be validated." True, you can check the file's grammar, but you can't validate that a given attribute must be a class in your program, for instance. With code-based config, you can.
</ul>