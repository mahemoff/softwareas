---
id: 773
title: 'Events Last Week: Web Fonts, Social Design Patterns, BT Dev Day, Real-Time Javascript'
date: 2010-01-25T00:37:16+00:00
author: admin
layout: post
guid: http://softwareas.com/events-last-week-web-fonts-social-design-patterns-bt-dev-day-real-time-javascript
permalink: /events-last-week-web-fonts-social-design-patterns-bt-dev-day-real-time-javascript/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574576"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - CSS
  - CSS3
  - Design Patterns
  - Fonts
  - html5
  - Javascript
  - NodeJS
  - Web
---
Last week saw a confluence of excellent events. In  the same week as a house move, it proved to be a week of much learning and little sleep. I'd hoped to do a better write-up, it never happened, a combination of being too busy and new MAC BATTERIES SUCK, meaning the lappy couldn't last through the whole session. But fortunately, I have some links to point to. Here's a quick summary anyway, along with the linkage.

<h3>Web Fonts at London Web Standards</h3>

<a href="http://www.londonwebstandards.org/2010/01/lws-january-web-fonts-with-ben-weiner-live-blog/">@otrops captured the live notes in glorious detail</a>, as did <a href="http://www.boogdesign.com/b2evo/index.php/2010/01/19/lws-january-web-fonts?blog=2">Rob Crowther</a>.

Ben is ideally placed to cover the brave new world of web fonts, being a web maker who studied fonts at uni. He walked us through the evolution of font hacks on the web: image with alt tag; CSS background image with text pushed off the page; rendering with Flash (<a href="http://www.mikeindustries.com/blog/sifr">SiFR</a>); rendering with Canvas or SVG (<a href="http://cufon.shoqolate.com/generate/">Cufon</a>, <a href="http://typeface.neocracy.org/">TypeFace.js</a>), using JSON-based font spec data. It all leads up to the holy grail: @font-face.

Great, so we have @font-face, but issues remain:
* The foundries - Mark Pilgrim, in no uncertain terms, <a href="http://diveintomark.org/archives/2009/04/21/fuck-the-foundries"></a>complains the font vendors are stuck in the dark ages of the printing press</a>, in their resistance to support @font-face. This seems to be changing with <a href="http://people.mozilla.com/~jkew/woff/woff-spec-latest.html">WOFF</a>, a web-only format that seems to placate the foundries, who worry their fonts will be stolen. It seems more like a symbolic gesture, since the data could still be converted and in any event the print fonts could still be appropriated, but the foundries are feeling more reassured and making signs they will go along with it.
* Performance issue - Bandwidth issues and Paul Irish's "flash of unstyled text", where the user notices the font change once the fancy @font-face font has been downloaded.
* Compatibility - IE has long supported font-face, but with EOT format fonts, and that remains the case. You therefore need both types of fonts, and licenses will generally not give you both.

<h3>Social Design Patterns</h3>

I was, needless to say, psyched about this. Yahoo! has been the closest thing to a realisation of the inspiring design pattern vision of the mid-late '90s. Patterns on the web, for both its own employees and the wider community to learn from and evolve. These are social design patterns mined by Christian Crumlish (@mediajunkie), in many respect the closest thing software has to an analogy of building architecture, where design patterns originally came from.

There are 96 patterns in all and I'm looking forward to poring through them. In these patterns are hundreds of people-years' experience of observing real-world social systems. In my own pattern work, I've found it necessary to articulate the overarching design principles behind the patterns. Pattern languages should be opinionated, so it's a good thing to make explicit your criteria for filtering design features. Christian has followed this model too, and identified 5 overarching principles:

* Paving the cowpaths. Facilitating the patterns that are already happening, rather than imposing your own invented process. Also means evolving with your users, ev dogster started as photo sharing but evolved to social network.
* Talk like a person.
* Play well with others. Open standards, mashups, etc. "if you love something, set if free"
* Learn from games.
- game UI concepts
- designing the rules, but ultimately letting the people who come into the space finish the experience themselves.*
* Respect the ethical dimension.

See <a href="http://www.designingsocialinterfaces.com/patterns.wiki/index.php?title=Main_Page">the wiki</a> or <a href="http://www.amazon.com/Designing-Social-Interfaces-Principles-Experience/dp/0596154925">the book</a> for more details.

<h3>BT Developer Day</h3>

This was an internal conference for BTers in London covering a range of general tech trends, and also being a chance to get together and talk shop. The agenda included talks on Scala, Rails, Kanban, iPhone development, and even a lightning talk from @psd on the horrors and delights of APL.

<a href="http://docs.google.com/present/edit?id=0AY-4v1wFiVhuZGNwbjVmM3JfMjdkdmdtNTRnNA&hl=en">I gave a talk on Embracing the Web</a>, emphasising open standards and the supreme primacy of <a href="http://paulirish.com/2009/cornify-easter-egg-with-jquery/">Konami Cornification</a>.

<h3>Real-Time Javascript</h3>

At the Javascript meetup, a great talk on NodeJS and WebSockets. NodeJS is coming on thick and fast, and Makoto Inoue showed how the technology plays nicely with WebSockets. WebSockets are all about Comet-style interaction, so  expect to see a lot more of this combo in the next couple years.

Luis Ciprian, visiting from Brazil, gave us an overview of XMPP and talked us through a real-time web app - a basketball score and conversation tracker - using XMPP.

Fin.