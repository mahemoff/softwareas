---
id: 127
title: AJAX and the Great Data Cloud in the Sky
date: 2005-05-18T07:13:03+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-and-the-great-data-cloud-in-the-sky
permalink: /ajax-and-the-great-data-cloud-in-the-sky/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572210"
  - "375572210"
categories:
  - HumansAndTech
  - Links
---
Office apps, backup, calendars - trying to store it online was all the rage of the mid-90s. By 2000, we would be hopping on our flying scooters and whizzing past the great data cloud in the sky.

Well, it was nice to dream.

Here are two major reasons it never happened:

* Options for rich clients - like Java applets and downloadable applications - were never feasible for a range of reasons, meaning that web applications became the only realistic choice. But web applications gave a lousy user experience and were hampered by portability issues.
* Trusting the host. Are you crazy? You want me to store my prized data on someone else's box?

Well, AJAX is a big step towards rich clients, and what we're seeing now will only get better with emerging patterns and frameworks. [GMail](http://gmail.com) and [Backpack](http://www.backpackit.com/) and the thousands of wikis are all examples of web applications with important data being stored server-side.

**But right now, you have to trust the host with your data. Feasible in some cases, but it would be ideal if data could be encrypted server-side. So a big challenge right now is to work out how web applications can deal with encrypted data.**

It turns out that **AJAX may well offer a viable solution to server-side encryption**. For the past couple of weeks, Richard Schwartz has been [talking about how an AJAX application could decrypt on the fly](http://smokey.rhs.com/web/blog/PowerOfTheSchwartz.nsf/d6plinks/RSCZ-6C5G54). The idea is this: in the past, decryption in the browser would have meant a Java applet - with all the usual Java problems - or Javascript-based encryption. But **Javascript can't remember data between page loads, so the user would have to type the passphrase each time** (or use frames, which is feasible though messy). **An AJAX application need load only once, so the user would only have to enter the password once per session**. Richard has a [proof-of-concept demo](http://aam.ugpl.de/node/1060) too.

There's also some [further discussion about how practical this idea is](http://smokey.rhs.com/web/blog/PowerOfTheSchwartz.nsf/d6plinks/RSCZ-6CCMCD). Having to type your password in each session is certainly an issue, but not a showstopper in my view, at least not for techie users. The reason is because of browser plugins. As Richard mentions, it could be solved on Firefox with a GreaseMonkey script. The reality is, it could be solved on IE too with the right plugin. So this is an example of [progressive enhancement](http://adactio.com/journal/display.php/20050308163812.xml). You can type your passphrase in if you need to, but install this plugin to avoid it.