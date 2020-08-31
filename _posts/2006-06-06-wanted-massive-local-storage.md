---
id: 306
title: 'Wanted: Massive Local Storage'
date: 2006-06-06T22:52:53+00:00
author: admin
layout: post
guid: http://www.softwareas.com/wanted-massive-local-storage
permalink: /wanted-massive-local-storage/
dsq_thread_id:
  - "375572925"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Dojo
  - Firefox
  - Flash
  - Links
  - Local Storage
  - Storage
---
Local storage - beyond 2KB cookies - is now a step closer with <a href="http://ajaxian.com/archives/firefox-2-client-side-storage-and-a-lot-more">the latest Firefox effort</a>. You get a local storage API like this:
[javascript]
sessionStorage.setItem(..)
globalStorage.namedItem(domain).setItem(..)
[/javascript]

The fantastic thing is Brad Neuberg's Dojo work means we can code independently of the local storage mechanism. Since <a href="http://codinginparadise.org/weblog/2005/08/ajax-internet-explorer-has-native.html">IE also has local storage</a>, as well as Flash, most bases are covered, or soon will be: Anyone with EITHER IE or Firefox or Flash will have local storage. (Incidentally, we had a discussion in the comments on Ajaxian about the possibility of S3 and other remote bindings as well, which I'm guessing Brad will implement at some point.)

<strong>But what I'd like to know, what I'd really really like to know, are the limits for these various techniques</strong> (I think Flash is 10MB per domain, right?)

As I've said before, there are valuable applications of massive storage - hundreds of gigs, e.g. media players that store data server-side, but cache content locally to cut down on the need for streaming from the server. Hopefully, these storage technologies won't try to second-guess the imagination of web developers by setting a dumb arbitrary limit that "no-one would ever need more than", like 100MB or 1GB or whatever.

<strong>If there's room on my hard drive, and I trust the domain, let me store as much as I please.</strong>