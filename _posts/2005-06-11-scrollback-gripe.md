---
id: 145
title: Scrollback Gripe
date: 2005-06-11T10:07:00+00:00
author: admin
layout: post
guid: http://www.softwareas.com/scrollback-gripe
permalink: /scrollback-gripe/
dsq_thread_id:
  - "375572329"
  - "375572329"
categories:
  - HumansAndTech
---
**Why is the default scrollback setting always so small?** This applies to DOS, XTerms, terminal emulators like putty (which could really do with a way to save the scrollback setting too).

**How much memory does a 10,000 line scrollback cost?** Let's knock ourselves out and assume it's full unicode - four bytes per character. On 80 wide, that's 320 bytes per line. So **the entire scrollback is [3.2MB](http://www.google.com/search?q=%2810%2C000+*+320%29+%2F+1000)**.
Being even more hedonistic, let's have ten such terminals, for a total of 32MB. Modern computers come with 1GB or more, so the cost is negligible, and any installer should make use of the computer's capabilities. Benefit of not losing vital information: priceless.