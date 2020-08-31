---
id: 717
title: Live Blogging Open Source Show and Tell (OSSAT) at TheTeam, November, 2009 (Part 2)
date: 2009-11-26T20:38:51+00:00
author: admin
layout: post
guid: http://softwareas.com/live-blogging-open-source-show-and-tell-ossat-at-theteam-november-2009-part-2
permalink: /live-blogging-open-source-show-and-tell-ossat-at-theteam-november-2009-part-2/
aktt_notify_twitter:
  - 'no'
dsq_thread_id:
  - "493904984"
categories:
  - SoftwareDev
tags:
  - Games
  - iphone
  - open source
  - phonegap
---
<em>standard live blogging warning</em>

Continuing on from <a href="http://softwareas.com/live-blogging-open-source-show-and-tell-ossat-at-theteam-november-2009-part-1">part 1</a> ...

<h3>Phil Hawksworth: Playing with Each Others' Toys</h3>

Phil describes the open source spectrum, from open-fan to open-curious to open-skeptic.

Open source is about sharing, so in that spirit, he's going to show us some toys he's made.

First up, <a href="http://polaroiderizer.com">Polaroiderizer</a>. One of his lessons from this was don't register a domain name that can be spelt and pronounced in many different ways! But back to Polariser...

The tool is made with simple technologies, requiring nothing more than some text files. HTML and CSS, JQuery, Flickr API. Able to be put together in just a couple of evening's work.

<a href="http://polaroiderizer.com"><img src="http://www.hawksworx.com/journal/wp-content/uploads/2009/02/polaroiderizer-a-slideshow-from-your-flickr-tags-2.png"></a>

Next specimen is <a href="http://github.com/philhawksworth/pinboard">Pinboard</a>. Similar tech. This time, there's a server, so he's used the excellent Sinatra. Along with Ruby and SQLite. He did the whole thing in Heroku, pushing to it via Git.

And then there's <a href="http://vlolly.com">vlolly</a>, Phil's ticket to an early retirement as soon as it goes viral. Another open source project with Ruby, using base62 gem to generate unique IDs.

<h3>Rain Ashford: Open Source Gaming for Handhelds</h3>

Having convinced us she is a true gaming geek, Rain walks through a few of the nicer open source games out there, including:

* Malice
* <a href="http://www.mrdictionary.net/lemmings/">Lemmings</a>
* <a href="http://marc-abramowitz.com/word_up/iphone/">Word Up!</a>
* Meteorea
* <a href="http://www.ds-scene.net/?s=viewtopic&nid=4124">Setsuzoku no Puzzle</a> (hosted on "DS Scene" so it <em>must</em> be cool)
* <a href="http://tobw.net/index.php?cat_id=3&project=Pocket+Physics">Pocket Physics</a>
* NitroTracker
* FreeDroid Classic (based on C64 "Paradroid")
* XRoar (Dragon emulator for DS and GP32)
* Nethack (DS and GP32 ports)- still going on strong

This session yielded the most challenging question of the night: Can you smell a wumpus?

<h3>Robbie Clutton: iPhone Dev</h3>

What's all this objective C? A bit like C and C++, but also message based like Smalltalk, which is dynamic but not, and object-based like Java. In other words, it's a different paradigm to what you're probably used to and it gets tricky working out which languages to take design patterns from.

When Robbie started looking at how developers can embed a web view into their app, he started wondering about the possibilities of developing an app that's mostly a plain old web app. Doing this would make development incredibly easy and you could get data from the local device in addition to the cloud. However, you don't get any device integration, and some events like gestures don't translate well.

Enter <a href="http://phonegap.com">Phonegap</a>. It's open source, cross device, and gives you integration with native features like vibration and the accelerometer. The way they do this is quite neat - your app basically connects to a phonegap server. So you do things like vibration by making standard Ajax calls. (The calls actually go to URLs with "gap://" protocol). Demonstrating the power of open source with a strong community, Robbie's submitted patches which have gone back into the product.

HTML 5 is a better way to do it in some respects. One of the obvious downsides is it doesn't show up as a native app, though you can still provide a HTML5 manifest so the app loads straight from the phone. There's also the question of talking to specific device features. You can do it in a limited form with device-specific meta-tags, but of course it ruins the whole standards-based approach to web development; move to another phone and you've got a port job ahead of you.

One of the nice things about this approach is you can use it elsewhere too, e.g. if you can put the whole thing in standard HTML, CSS, and Javascript, you just create a simple XML file, run "adl application.xml", and you now have an Adobe Air powered desktop app.