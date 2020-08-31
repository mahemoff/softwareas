---
id: 618
title: JQuery IFrame Plugin
date: 2009-09-15T23:10:52+00:00
author: admin
layout: post
guid: http://softwareas.com/jquery-iframe-plugin
permalink: /jquery-iframe-plugin/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375141469"
categories:
  - SoftwareDev
tags:
  - Javascript
  - JQuery
  - Plugin
  - Project
  - Scrumptious
  - Web
---
<a href="http://www.nczonline.net/blog/2009/09/15/iframes-onload-and-documentdomain/">This article by Nick Zakas</a>, covering some technical issues in iframe loading, triggered me to  surface a JQuery IFrame plugin I made a little while ago, which supports loading IFrames. (I did <a href="http://twitter.com/mahemoff/statuses/3177377341">tweet it</a> at the time, though I've since changed the location.)

<a href="http://project.mahemoff.com/jquery-iframe/">JQuery IFrame plugin</a>

<a href="http://project.mahemoff.com/jquery-iframe/"><img style="width:400px;" src="http://img.skitch.com/20090915-k34qa5qjcxfht4axtrfdkcdni6.jpg"></a>

The plugin basically tells you, the programmer of the parent document, when your child iframe has loaded. It also has some other bells and whistles, like timing the load duration.

It's inspired by the use cases of WebWait (http://webwait.com) and the Scrumptious trails player (http://scrumptious.tv). Both are applications whose whole mission in life is to open up an external page in an iframe, and do something when it has loaded.

There's already an <a href="http://ideamill.synaptrixgroup.com/?p=6">IFrame JQuery plugin</a>, but it's to do with controlling what's inside the iframe, i.e. the situation which is only possible when the iframes are from the same domain. What I'm dealing with here is the parent knowing when the iframe is loaded, regardless of when it comes from and agnostic to what it does.