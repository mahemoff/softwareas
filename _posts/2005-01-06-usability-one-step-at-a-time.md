---
id: 38
title: Usability One Step at a Time
date: 2005-01-06T21:09:25+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=35
permalink: /usability-one-step-at-a-time/
categories:
  - HumansAndTech
---
Martin Fowler is talking about <a href="http://martinfowler.com/bliki/SpreadingIncrementalism.html">incrementally improving specialised requirements such as usability or security or internationalisation one step at a time</a>, in much the same way as agile projects should enhance functionality one step at a time.

On **usability**, it can be done. Indeed, one of the nice things about agile projects is you can get more rapid feedback from users, and iterative development is the holy grail of usability. We touched in this in our Extreme [Usability workshop](http://www.xpday.org/slides.php) last November.

However, there is a **big downside: user training**. **Many users are too busy to learn new interfaces.** So sometimes, you can come refactor your system into something more parsimonious --- less "if...then" logic, less complicated domain objects, so it's easier for developers. This might be necessary to help you cope with an upcoming requirement.

That should be great news for users too as it simplifies their mental model, but what if they're already familiar with the old model? Unlike developers, they're not thinking about the system design all day long; they're focusing on getting the job done, and they've probably internalised many aspects of the system.  If you go and observe users dealing with a complicated system, you'd be amazed at how creative they can be in finding workarounds!

Thus, a challenge for agile development remains: how to incrementally develop system concepts while providing minimal interruption to users. I'm not familiar with any HCI research on this topic, perhaps it is a good research opportunity in a world becoming more agile.

On **internationalisation (I18N)**, [this paper](http://mahemoff.com/paper/reqsi18n/) describes some of the processes. It's definitely a multi-stage process, with localisation-enabling taking place before localisation itself. Here, there is a very obvious way to develop incrementally: develop the English (or whatever market) product first, and ONLY THEN enable it. Doesn't work for all cases, but it's amazing how many projects have done a big I18N framework upfront, only to release in one language. With unit tests and modern IDEs, it shouldn't be difficult to extract messages out later on.