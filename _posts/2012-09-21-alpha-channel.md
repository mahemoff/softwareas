---
id: 1830
title: Alpha channel
date: 2012-09-21T02:08:18+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1830
permalink: /alpha-channel/
categories:
  - SoftwareDev
tags:
  - CSS3
  - Design
---
I'm not much of a visual designer, but here's a subtle little use for alpha channel I found while build a related episode feature. (You may have to squint a bit here or alternatively zoom in.)

In the before pic, we have dark text on a dark-and-light texture:

<a href="http://imgur.com/S6siG"><img src="http://i.imgur.com/S6siG.png" title="Hosted by imgur.com" alt="" /></a>

The text blends into the background too much, so we can sharpen it up with a subtle background (#eee):

<a href="http://imgur.com/Xrlig"><img src="http://i.imgur.com/Xrlig.png" title="Hosted by imgur.com" alt="" /></a>

Better, but observing closely shows the discontinuity. So instead of full light-gray, let's blend it into the background. Here I used a 0.5 alpha channel (<tt>rgba(240,240,240,0.5)</tt>) and to make the transition even less jarring, a 5 pixel border radius too. (I suppose I could have added a box shadow for max combo.) I think it's considerably sharper now, but without any noticeable background.

<a href="http://imgur.com/5s0lA"><img src="http://i.imgur.com/5s0lA.png" title="Hosted by imgur.com" alt="" /></a>