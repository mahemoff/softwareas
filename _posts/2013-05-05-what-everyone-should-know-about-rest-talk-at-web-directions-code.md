---
id: 1921
title: 'What Everyone Should Know About REST: Talk at Web Directions Code'
date: 2013-05-05T04:34:27+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1921
permalink: /what-everyone-should-know-about-rest-talk-at-web-directions-code/
categories:
  - SoftwareDev
tags:
  - Presentation
  - REST
---
Here are the slides:

[Slides: What Everyone Should Know About REST](http://prez.mahemoff.com/rest4all)

<a href='https://twitter.com/uxmastery/status/330166800627142656'>![Sketchnotes](https://pbs.twimg.com/media/BJT89LRCEAEaI8H.jpg:large)</a>

Thanks UX Mastery for the sketchnotes, they are awesome! (Seriously, I would be much more swayed to speak at any conference with sketchnotes because it's a straightforward permanent memento, a better snapshot than slides or video.)

Overall, it was great to be associated with another fine Web Directions conference and the Melbourne Town Hall venue was amazing. I only regret that we were so busy scrambling on the Android app, after launching just a few days earlier, to be around the whole time. But this being my hometown &mdash; I'll be back!

### Talk Structure

I spoke at [Web Directions Code](http://code13melb.webdirections.org/) on Friday, a talk on REST. I've been putting a lot of this into practice lately, and the talk was really an attempt to convey the main practical things every developer should know. The structure was:

* Everyone should know about REST because it's not just about websites anymore. Devices, whether computers, fridges, or wearable glasses - are connected, and device-to-device communication happens with web standards, i.e. HTTP. The talk covered three things about REST: Simplicity+Consistency; Security; Caching.
* Simplicity+Consistency: Emphasising Developer Experience (#devexp) was a way to frame the general concepts, ie URLs, HTTP methods, response types.
* Security: How the web is becoming SSL-only, and various authentication schemes. I referenced [the latest Traffic and Weather](http://player.fm/1Xdnm), which has a good discussion on this.
* Performance+Scalability: Mostly about caching. I've been musing on REST caching quite a bit for Player FM's API ([most recently](https://plus.google.com/106413090159067280619/posts/jKzaYxgvHTY) thinking about a kind of reverse patch protocol, where the server can send out diffs that get cached), and explained some of the standards and tricks for squeezing efficiency out of the network.

### What Wasn't Covered

* I didn't go into the REST acronym or the general theory of REST as an architectural pattern arising from specific forces.
* SSL and caching. Good Twitter conversation afterwards about this point, that you can't cache in the middle of an SSL connection. The answer is to split the connection in the middle and run SSL on either side, with a trusted cache seeing plain-text in the middle. This is how Cloudflare works, and the CEO Matthew Prince [chimed in](https://twitter.com/eastdakota/status/329822448654643200) to say it will be free soon. (At least, SSL from client to Cloudflare.) So that means the SSL-protected web could triple overnight.