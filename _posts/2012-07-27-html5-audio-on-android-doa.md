---
id: 1787
title: 'HTML5 Audio on Android: DOA'
date: 2012-07-27T17:23:28+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1787
permalink: /html5-audio-on-android-doa/
categories:
  - SoftwareDev
tags:
  - audio
  - html5
---
[This Android bug with HTML5 audio is awful.](http://stackoverflow.com/questions/11035890/html5-audio-behavior) After a phone call or SMS, it resumes playback EVEN IF the audio was paused and EVEN IF the browser isn't active. I just added a +50 bounty to this question as I still can't figure how to prevent playback from happening.

Try it yourself on Android Browser:
[http://jsbin.com/welcome/5289](http://jsbin.com/welcome/5289)

Meanwhile Chrome audio is so temperamental it shuts down when the screen turns off, a critical flaw which no-one is prepared comment on ([http://code.google.com/p/chromium/issues/detail?id=121898](http://code.google.com/p/chromium/issues/detail?id=121898)).So much for open web standards.

And you wonder why native apps are eating HTML5's lunch. Even with packaging from PhoneGap and it's building apps on a house of cards. Until the default Android runtime is Chrome, and Android Chrome gets up to parity with Mobile Safari and beyond, there's not much point using HTML5 to develop anything serious on Android, not when the native platform keeps running ahead on turbo mode.

[Cross-posted and modified from G+]([https://plus.google.com/106413090159067280619/posts/8JSv7WU6kMK](https://plus.google.com/106413090159067280619/posts/8JSv7WU6kMK))