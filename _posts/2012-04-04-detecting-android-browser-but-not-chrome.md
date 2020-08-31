---
id: 1621
title: Detecting Android Browser, But Not Chrome
date: 2012-04-04T19:50:48+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1621
permalink: /detecting-android-browser-but-not-chrome/
categories:
  - SoftwareDev
---
"A browser’s user-agent string isn’t an identifier, it’s a reverse-chronological history of the web."
- [Jeremy Keith](http://adactio.com/journal/5289/)

I have to perform evil browser-sniffing because Android Browser is ... special. A little slow and using SoundManager, a little different.

Well, today I installed Ice Cream Sandwich (Android 4.0) on the Nexus today, much hat tips due to [the Cyanogenmod wiki guide](http://wiki.cyanogenmod.com/wiki/Nexus_S:_Full_Update_Guide). So I can finally try out Chrome on Android, and it's actually sweet. In fact, on first impressions, it has more in common with Chrome on Desktop than it has with the standard Android Browser. So I had to update the evil sniff code to _exclude_ Chrome.

Both browsers present as "Android" and "Mobile". Chrome additionally presents as "CrMo". So my new CoffeeScript to detect Android Browser, but not Chrome, is this:

[code]
isAndroid = ->
  ua = navigator.userAgent.toLowerCase()
  ua.indexOf("android") != -1
    and ua.indexOf("mobile") != -1
    and ua.indexOf("crmo")==-1
[/code]

Update: And as Pornelski points out, there's also Firefox, Opera, et al. How I end up grouping them is still up in the air, so consider this a work in progress.

Originally adapted from [here](http://davidwalsh.name/detect-android).