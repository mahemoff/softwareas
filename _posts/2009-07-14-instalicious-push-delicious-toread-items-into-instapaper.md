---
id: 559
title: 'Instalicious: Push Delicious &#8220;ToRead&#8221; Items Into Instapaper'
date: 2009-07-14T22:44:31+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=556
permalink: /instalicious-push-delicious-toread-items-into-instapaper/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375574304"
categories:
  - SoftwareDev
tags:
  - Announcement
  - delicious
  - instapaper
  - iphone
  - Mashup
  - Project
  - Python
---
<strong>Update:</strong> Moved instalicious to <a href="http://github.com/mahemoff/Instalicious/tree/master">GitHub</a>. The main change I made since posting this was to stop items reappearing in Instapaper once you've deleted them; the sync process was causing them to be pushed from Delicious again. The script now changes the "toread" tag to "instaliciousd" (configurable name), so "toread" items will only be pushed once.

<img src="http://picupper.com/2009/07/14/instapaper_shot2.png">

<a href="http://instapaper.com">Instapaper</a> lets me read stuff later - I hit a bookmarklet when I'm reading it and I can see it later on my browser or in iphone, or print articles in a newspaper format. The problem is, I'd rather add that stuff to my Delicious stream so I have a permanent record, others can see it, and it plays nicely with in mashups.

So I decided I want a way to bookmark things in Delicious as normal, but still have them appear in Instapaper. Here's the script repo:

<strong><a href="http://github.com/mahemoff/Instalicious/tree/master">Instalicious repository at GitHub</a></strong>

Instalicious is a little Python script that plucks out items tagged "toread" - or some other configurable tag - and pushes them to Instapaper. Fortunately, both services have easy APIs (<a href="http://blog.instapaper.com/post/73123968/read-later-api">Instapaper API</a>; <a href="http://delicious.com/help/api">Delicious API</a>), and in the case of Delicious, there was even a pleasant <a href="http://www.michael-noll.com/wiki/Del.icio.us_Python_API">Python binding to the API</a>. Also, the Instapaper API happily doesn't create duplicates when you send it something you've already sent...so Instalicious doesn't have to remember what it sent. It just dumbly polls Delicious and sends it over to Instapaper.

Now you can <a href="http://softwareas.com/designing-like-a-pollyanna-have-your-cake-and-eat-it-too">have your cake and eat it</a> :). 