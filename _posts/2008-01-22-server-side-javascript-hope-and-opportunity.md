---
id: 415
title: 'Server-side Javascript: Hope and opportunity'
date: 2008-01-22T23:50:35+00:00
author: admin
layout: post
guid: http://www.softwareas.com/server-side-javascript-hope-and-opportunity
permalink: /server-side-javascript-hope-and-opportunity/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375573468"
categories:
  - SoftwareDev
tags:
  - AppJet
  - Javascript
  - Links
  - Server-Side Javascript
---
<b>Update:</b> See also http://mini.softwareas.com/why-server-side-javascript

<a href="http://almaer.com/blog/the-development-circle-of-life">Dion's cartoon</a> resonated with me:

<a href='http://almaer.com/blog/the-development-circle-of-life'><img src='http://picupper.com/2008/01/22/developmentcircleoflife.png.jpg'/></a>

Resonated because only last night I was thinking it's about time I actually started playing with server-side Javascript, and wrote my first, extremely dumb, <a href="http://animals.appjet.net/">AppJet app</a>. I will hopefully make it, like, actually do something at some stage.

I've discussed the potential of <a href="softwareas.com/phobos-server-side-js-redux">server-side Javascript</a> before, and the more I think about, the more I like it. Javascript is a sophisticated language and, by now, a language very familiar to many professional web developers.

The real gap is in server-side frameworks and hosting. There's no <a href="beust.com/weblog/archives/000474.html">"killer app"</a> Javascript server, a la what Rails did to Ruby. I haven't even heard of most of <a href="http://en.wikipedia.org/wiki/Server-side_JavaScript">the SSJS frameworks listed in Wikipedia</a>. Furthermore, try finding a virtual host that supports Javascript! You would practically need one that support Java, so you can run Rhino or whatever, and few virtual hosts do that. At least Python and Ruby were running on many virtual hosts before Django and Rails showed up. For that reason, the model pursued by AppJet seems worthy. If they can come up with a solid virtualisation environment for Javascript, they may be on to a big winner. They could be the BEA or JBoss of 2015 (2010 seems a bit early for all that!). And if the rumour is true they're using Scala, they'll get doubleplus-coolness votes for language selection.