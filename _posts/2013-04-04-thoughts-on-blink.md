---
id: 1910
title: Blinking WebKit
date: 2013-04-04T00:54:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1910
permalink: /thoughts-on-blink/
categories:
  - SoftwareDev
tags:
  - Blink
  - Chrome
  - Chromium
  - WebKit
---
* **Speed.** When Alex Russell talks about greater speed [1], I take it fractally. At micro level, it means actual day-to-day web development and debugging is faster; and at macro level, it means browsers and web standards move faster. Google works the same way; it is a company which cares deeply about speed; at macro level, that means pushing Kurzweil's broader interpretation of Moore's Law to its limit, and at micro level, it means great victory for every nanosecond that can be shaved off a search query.

* **Inevitable.** The writing has been on the wall for years. Chrom{e/ium} has been heavily driving WebKit and it's only natural they should want to lead the project. Cutting-edge WebKit is already there on desktop and mobile; in the future, it will need to be there in more contexts, i.e. Android webviews, Google TV or what becomes of it, Glass, cars, etc.

* **Dart.** I can't get a grip on how much Dart is growing, I'm too out of the loop. But if it is indeed growing to the point that it gets to survive and be blessed internally, it will be part of Blink. No question.

* **Safari.** I've read some people say to the effect "you're doing it wrong if not already testing on Safari as they're already different". Well yeah if you're writing a mission-critical trading app. But let's be honest; this business about testing on all browsers comes with a big wink and a sizeable nudge. Most of us _can_ and _do_ get by testing only occasionally on Safari. Even more so for Windows developers who don't even have access to a modern Safari. I don't see Apple adopting Blink anytime soon, I'm not even sure the importance of this fork will filter up to Apple's seniors for some time. And this is a good old fashioned fork; WebKit and Blink *will* be significantly different. So the net effect for developers is more testing on Safari. And compensated by less testing on ...

* **...Opera.**  My heart sank a little for Opera on reading this news; so it's good to know Opera was in on the secret. If not when they made the decision to adopt WebKit, then at least some point before the Blink news dropped. Blink will certainly be stronger for Opera's contributions.

* **Samsung.** Samsung has to be considered a major part of today's browser ecosystem. They get to pick the browser that goes into most smartphones after all, and it's no secret they are on a collision path with Google. Last night's news of a major collaboration with Mozilla (on Servo) is more evidence of that. Should Samsung start shipping Firefox as the default browser, the web really will have four major mobile engines (including IE here). It feels like battle lines have been drawn, but that's probably more about the coincidence of timing. Also worth mentioning Amazon as a similar company with potential to grow into a major influence on the web ecosystem, via Silk. One can assume they will adopt Blink.

1. http://infrequently.org/2013/04/probably-wrong/