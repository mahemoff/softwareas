---
id: 254
title: OSX Screenshot Script
date: 2005-12-27T11:15:32+00:00
author: admin
layout: post
guid: http://www.softwareas.com/osx-screenshot-script
permalink: /osx-screenshot-script/
dsq_thread_id:
  - "375462486"
  - "375462486"
categories:
  - SoftwareDev
tags:
  - Apple
  - Bash
  - OSX
  - Screenshot
---
<a href="http://www.flickr.com/photo_zoom.gne?id=2130065&size=s"><img style="float: right; margin: 7px;" border="0" src="http://static.flickr.com/2/2130065_fa909eca28_m.jpg"/></a>

<b>Let's say you wanted to capture a few images for a fade effect, which means you need a sequence of rapid screenshots. Here's a script I've been using:</b>
> i=0 ; while [ 1 ] ; do i=`expr $i + 1` ; screencapture  -C $i.png ; sleep 0.1; done

Hit ctrl-c to kill it, then view the sequence with gqview or something. Then use the very cool [Flysketch](flyingmeat.com/flysketch/) to grab the same position each time. Caveat: The 0.1 millisecond interval is optimistic, the powerbook seems to handle only about 3 pics per second.

The camera sound effect helps a lot as you know precisely which instant got taken and also creates the requisite fashion shoot ambience.

Here's a sequence with a fade effect (<a href="http://ajaxpatterns.org/One-Second_Spotlight">One-Second  Spotlight</a>) from [Everybody's favourite fade effect website](http://backpackit.com/).

<a href="http://imageshack.us"><img src="http://img380.imageshack.us/img380/9807/backpackwillfade5rh.png" border="0" width="325" alt="Image Hosted by ImageShack.us" /></a><a href="http://imageshack.us"><br /><img src="http://img380.imageshack.us/img380/9041/backpackfading4ez.png" border="0" width="325" alt="Image Hosted by ImageShack.us" /></a>
<a href="http://imageshack.us"><br /><img src="http://img380.imageshack.us/img380/662/backpackfaded0uj.png" border="0" width="325" alt="Image Hosted by ImageShack.us" /></a>

The alternative would be to record it as a screencast and pick out the frames. I was using [Wink](http://www.debugmode.com/wink/) under Linux, but haven't looked into OSX tools, any suggestions?