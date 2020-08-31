---
id: 1526
title: 'The Boot2Gecko Developer Experience: An Interview with Mozilla&#8217;s Jonathan Nightingale'
date: 2012-03-05T21:37:16+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1526
permalink: /the-boot2gecko-developer-experience-an-interview-with-mozillas-jonathan-nightingale/
categories:
  - SoftwareDev
tags:
  - Boot2Gecko
  - Firefox
  - html5
  - Mobile
  - Mobile Web
---
A surprise bonus of last week's MWC trip was the coincidental launch of [Boot2Gecko](https://wiki.mozilla.org/B2G), Mozilla's operating system based on Firefox (Gecko being Firefox's underlying layout engine and B2G being the unofficial brand name for now). They made a joint announcement with Spain's Telefonica (O2 and GiffGaff's parent company) with the expectation to release a commercial offering this year (no commitments yet though).

Continuing my "a conference is worth more than 140 characters" resolution, I had a chance to sit down with Mozilla's Senior Director of Firefox Engineering, [Jonathan Nightingale](http://blog.johnath.com/) and understand some of the technical issues around the new OS.

<iframe width="420" height="315" src="http://www.youtube.com/embed/zC8e-zXJ9OY" frameborder="0" allowfullscreen></iframe>

<br/>Key points from the video, as well as speaking to some of the other Mozillians:

* The device could be very cheap, $60 for a SIM-free device is a figure I heard.  Needless to say, if they can achieve a price point like that, it will be music to carriers' ears and simultaneously light up the HTML5 developer community. At 10:00, Jonathan mentions that Telefonica sees the opportunity to produce a smartphone that's "interactive, smooth, high quality, with a good app selection, that is one-tenth the cost of an iPhone". From what I've heard, this is because of two factors: the target hardware is open and patent-free, and the HTML5 runtime is built over a thin Linux core, so various layers are eliminated.
* It boots fast, about 14 seconds (I thickly say 4 seconds in the video but I was counting from the splash screen...my argument is invalid). Bearing in mind this is a very early concept, the final version will hopefully be even faster, though it's possible extra services may make it slower too.
* Everything is HTML5. The launcher, dialler, camera, gallery, et al. And what's more ...
* ... On the dev build, as Jonathan demos, View Source is available everywhere! On all the apps, and that includes those "system" apps above (launcher, dialler, etc).
* The Mozilla Marketplace is not exclusive to B2G. It will run on other devices where Firefox runs, like Android. (It turns out that Android apps can be permissioned to add multiple URL shortcuts to the Android launcher, so once a user installs the market, they can install apps directly on the launcher.) This is a little like the Chrome Web Store, which is the app distribution mechanism for ChromeOS, but also works on regular Chrome across the different OSs it runs on.
* Mozilla's keen to cultivate an ecosystem of multiple marketplaces with different verticals and business models. They offer their own marketplace, but will happily embrace others.
* No immediate plans for extensions or a NodeJS service layer like WebOS runs, but Moz is very open to feedback via the standard channels.

[PPK argued in last week's Web Ahead](http://5by5.tv/webahead/17) we may well see a shift away from Android in the next year as carriers come to terms with Google's Motorola acquisition. It's not for certain, but I did hear people echo this view at MWC. Boot2Gecko will be a key part of the current movement among the smaller OSs to embrace HTML5 developers. And if the price point means developers can easily get their hands on these devices, as opposed to the usual suspects who are awarded freebies by marketing departments, it stands a real chance in this market.

HTML5 developers should also check out [Christian's Boot2Gecko write-up](http://christianheilmann.com/2012/03/04/mobile-world-congress-boot-to-gecko-and-the-unknown-beast-called-html5/) for more info, as well as [the official Boot2Gecko Wiki](https://wiki.mozilla.org/B2G).