---
id: 972
title: The Secret to Quick Node Hacks is
date: 2010-09-25T18:06:53+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=972
permalink: /the-secret-to-quick-node-hacks-is/
dsq_thread_id:
  - "381402800"
categories:
  - SoftwareDev
tags:
  - Agile
  - Hackathons
  - Javascript
  - NodeJS
---
to ignore security and do everything local.

I'm at the inaugural <a href="http://ampedweb.org/">Amped</a> event, and you could immediately guess people were going to be using Node, from the fact they were breathing. So I pointed them to my <a href="http://softwareas.com/video-sync-with-websocket-and-node"Node Video Sync hack</a>, which is indeed a total hack.

<strong>Basically, you can do any multi-user app with a server of 10-20 lines. All you do is broadcast each user's actions.</strong> In fact, such a server would make a great open source project (but I'm otherwise occupied playing with PhoneGap and Android). Sure, Node makes servers easier, but for version 0.01, this is all you need. A video sync app would get messages like this:

<pre>
{ user: "john", time: "103094401", action: "join" }
{ user: "sue", time: "103095491", action: "join" }
{ user: "john", time: "103095822", action: "takeControl" }
{ user: "john", time: "103096111", action: "play" }
{ user: "john", time: "103096483", action: "fastforward", data: { position: 2.12 } }
{ user: "sue", time: "103098111", action: "takeControl"}
</pre>

This is trading off security for productivity. There's ZERO security here, because (at least the way I implemented the video sync) any user can forge a request from any other user. But that's the point: It's a hackathon. Unless you're at a security hackathon, security doesn't matter a hoot. Nor does maintability, readability, or most other -ilities.

If I was doing this for a "real" project, I'd start the same way. I'd be wasting my employer's/client's time if I was spending it if I did it any other way, since 9 projects out of 10 (&lt;/blatantly made-up stat&gt;) never get out of feasibility phase.

<img src="http://picupper.com/2010/09/25/logo.png"></img>