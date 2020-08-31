---
id: 544
title: 'Scrumptious: Conversations About Websites (and other resources)'
date: 2009-06-11T00:22:53+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=541
permalink: /scrumptious-conversations-about-websites-and-other-resources/
dsq_thread_id:
  - "375574232"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Ajax
  - Announcement
  - Javascript
  - Osmosoft
  - Scrumptious
  - tiddlyweb
  - TiddlyWiki
---
<a href="http://scrumptious.tv">Scrumptious</a> is a web framework I've begun working on at Osmosoft. It's a web app and web service for sharing bookmarks and comments about websites, and pretty much anything else with a unique URL. Things it is related to: Delicious (bookmarking), Digg (threaded comments), JS-Kit and Disqus (embedded comments with common identity across multiple sites).

<a href="http://img.skitch.com/20090610-bdeahfs32jq8htgabh4nb9ubyu.jpg"><img src="http://img.skitch.com/20090610-bdeahfs32jq8htgabh4nb9ubyu.jpg" style="width:400px;"/></a>

Scrumptious is open source, under the BSD license (meaning you can do just about anything you like with it). There are already <a href="http://3spots.blogspot.com/2006/05/delicious-digg-clones-and-open-source.html">many open-source clones</a> of this sort of thing, so why make a new one? There are a few reasons:

<ul>
  <li>Adherence to RESTful principles - Scrumptious is backed by <a href="http://tiddlyweb.com">TiddlyWeb</a>, a RESTful data service.</li>
  <li>A non-TiddlyWiki TiddlyWeb client - So far, people who have used TiddlyWeb as a server have used TiddlyWiki as a client. They do play nicely together, but TiddlyWeb is a powerful RESTful framework on its own. Part of the motivation for Scrumptious was to port the <a href="http://tiddlywiki.mahemoff.com/CommentsPlugin.html">TiddlyWiki nest comments plugin</a> to a generic JQuery plugin that could be used on any web page. (Comments are indeed implemented as a plugin right now, but more work needs to be done to extract it into something truly modular and reusable; for example, the plugin right now assumes comments are about a web page; also, they are tied to TiddlyWeb. Nevertheless, the app still does achieve the main purpose of demonstrating TiddlyWeb is a fine data service for generic web apps.)</li>
  <li>Demonstrating the power of URLs - In evangelising web standards, a very practical piece of advice is simply to associate a unique URL with each distinct resource. That's REST 101, but it's something lacking in many web apps. With a tool like Scrumptious, you get a comment system "for free" as long as each resource in your system has a unique URL. We'll be developing a similar framework for <a href="http://softwareas.com/as-we-may-think-url-trails">URL Trails</a> in the future, and the same principle applies: use unique URLs, and people can put your stuff in trails "for free".</li>
  <li>Flexible security model - Again, TiddlyWeb offers flexible permissioning, so you can use the app in different ways. e.g. a private conversation between colleagues; a public conversation (as with the demo), a publicly readable conversation where only certain individuals can contribute, etc. Likewise, TiddlyWeb offers flexible authentication, so you could hook into an organisation's LDAP system, use open ID, simple user-password pairs, or any other form of authentication you wish to use.
</ul>

Scrumptious is still at an early stage. Future work includes:

<ul>
  <li>Bookmarking - for now, there is only commenting rather than social bookmarking per se.</li>
  <li>Nested comments UI needs work to give it the same kind of UI as in the TiddlyWiki comments UI. e.g. show info like creator and creation data, and use suitable rendering and indenting.</li>
  <li>Graceful degradation - It would be possible to provide a basic system not requiring Javascript. This would be probably be done using TiddlyWeb plugins, though I'd also be interested in running the JQuery-powered web app on the server, using server-side Javascript.</li>
  <li>TiddlyWiki comments plugin harmonisation - As TiddlyWiki now ships with JQuery, it would be ideal if there was a single code base for the comments plugin, running in and out of TiddlyWiki. Indeed, I hope TiddlyWiki moves towards a general microkernel architecture, in which all plugins are useful outside TiddlyWiki. This is certainly becoming the case, with generic JQuery plugins being extracted for core activities like file saving, CSS applying, and wikifying.</li>
  <li>Browser extensions - instead of a bookmarklet, use a browser extension to show, for each page, if comments are available, as well as bookmarking info. (Similar to the StumbleUpon or Delicious Firefox extensions.) A good opportunity to get my hands dirty with <a href="https://jetpack.mozillalabs.com/">JetPack</a>.</li>
  <li>Login and identity management - while TiddlyWeb already provides the security and permissioning model, work is required to handle this at the UI level. For example, let anonymous users enter their email address and homepage, and/or register.</li>
  <li>User admin - for situations where users must be authenticated, some form of user management would be handy. Again, TiddlyWeb provides a good model for this - a "bag" of tiddlers has its permission specified in JSON, which may include a list of users for each access type, so you simply need to PUT and GET this if you are sufficiently permissioned (ie an admin). What's missing right now is a UI (in TiddlyWiki too, let alone standalone web apps).</li>
</ul>

Scrumptious Screencast:

<object width="400" height="300"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=5079811&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=5079811&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><p><a href="http://vimeo.com/5079811">Scrumptious</a> from <a href="http://vimeo.com/user960717">Michael Mahemoff</a> on <a href="http://vimeo.com">Vimeo</a>.