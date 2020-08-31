---
id: 1899
title: A Bash Logging Utility
date: 2013-03-08T01:36:54+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1899
permalink: /a-bash-logging-utility/
categories:
  - SoftwareDev
tags:
  - Bash
  - Logging
---
With a long-running script, it's convenient to see checkpoint log messages indicating what stage it's at and how long it's taken.

Most scripts simply run `date` to show the boring long date format: `Fri Mar 29 21:07:39 MST 2002`. Info overload! You don't want to know what month it is, whether you're in the middle of a weekend, or what timezone you're in! More to the point, you want to know how much time has elapsed, not what time it is now; you want to know the script's age.

So here's a little utility to make it easy. Just call "age" and it will output time since the script began in 00:00:00 format.

I also made another function "announce" which you can use to announce the current function is running. With larger bash scripts, I tend to break them into functions with a list of calls at the bottom; so I can quickly bypass unnecessary crunching by commenting out the call. "announce" makes it easy to see which is running. And if you wanted, you could easily automate announcing for each function...making [aspect-oriented](http://en.wikipedia.org/wiki/Aspect-oriented_programming) Bash the place to be.

<script src="https://gist.github.com/mahemoff/5113522.js"></script>