---
id: 714
title: Live Blogging Open Source Show and Tell (OSSAT) at TheTeam, November, 2009 (Part 1)
date: 2009-11-26T19:29:15+00:00
author: admin
layout: post
guid: http://softwareas.com/live-blogging-open-source-show-and-tell-ossat-at-theteam-november-2009-part-1
permalink: /live-blogging-open-source-show-and-tell-ossat-at-theteam-november-2009-part-1/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375377421"
categories:
  - SoftwareDev
tags:
  - drupal
  - html5
  - open source
  - ossat
  - Ubuntu
---
<em>standard live blogging warning</em>

I'm here at TheTeam offices in London Bridge, with a number of my Osmosoft colleagues for this open source event.

<a href="http://upcoming.yahoo.com/event/4516026/gb/London/Open-Source-Show-and-Tell/The-Team/">Event Announcement</a>

The agenda:

* Iain Farrell, Canonical - Ubuntu Update
* Julien Fourgeaud, Symbian - Managing the Symbian community
* Jeremy Ruston, Osmosoft - HTML5 and the slow death of Flash
* Leisa Reichelt, Disambiguity.com - Drupal 7 Update
* Phil Hawksworth, The Team - Playing with each others toys: Developing with open technologies
* Rain Ashford, BBC - Open Source Gaming for Handhelds
* Robbie Clutton, BT - iPhone development using web technologies


<h3>Canonical: The Ubuntu Developer Summit</h3>

Iain explains the process of updating Ubuntu. Happily enough, the release cycle is 6 months, coinciding nicely with these OSSAT events, hence the trend is set for an update each OSSAT.

Every 6 months, there's a big Ubuntu shindig; this is (I think) just after the last release ships. All ~240 employees invited and ~30 invited people from the community. Room for talks - the schedule is always evolving even during the conference - and spaces for just hacking. Very online too for those who can't make it - stereo recording in every room. All the audio, mixing, publishing, and so on is power by the magic of open source. Naturally.

The design process is generally speaking 6 months ahead of the development process, i.e. in cycle t, they're thinking about what they'll be developing in cycle t+1. For users, a 6 month cycle means lots of incremental improvements, as opposed to 

<h3>Julien Fourgeaud: Symbian's Community Programme</h3>

Nokia started as an alliance and Nokia then purchased Symbian Ltd. When that happened, there was a move to open source the code. Julien explains the ecosystem - 90 people maing up the foundation (people in US, UK, Finland, Japan, China, elsewhere) - working with a large community of consumers, ODMs, OEMs, and operators. They often run BOFs embedded in other conferences.

What's Symbian doing to get consumers what they want? They're creating initiatives to get agile and engage in dialogue going with consumers. [I would have liked to see more on this, but it sounds like they're just at the start of the path here.]

Of possible relevance to the next talk, <a href="http://www.symbian.org/">Symbian's portal</a> is a Flash-heavy representation of standard web technologies such as hyperlinks ...

<h3>Jeremy Ruston on HTML5 and the Slow Death of Flash</h3>

<img src="http://posterous.com/getfile/files.posterous.com/mahemoff/oXNqOjJF7bvE23xAn0Q8B8pDshCU210APzVxgKc9eyN87hPdVfQ9Fz3JY72Q/photo.jpg" style="width:400px;">

Jeremy points out he's dogfooding by presenting in <a href="http://www.osmosoft.com/cecily/">Cecily</a>, his  3D zooming and panning interface powered by open web technologies. He points out the anti-Flash vibe isn't new, with Jacob Nielson having declared Flash "99% bad" back in 2000. A few of the problems with Flash are:

* Battery drain
* Crashy
* Can't exploit hardware acceleration (except video and certain blitting operations) - the operations of HTML5 have been designed to take advantage of it
* Big opaque ball of bits - can't reach in and get at the data/content inside
* Controlled by media interests (e.g. to ensure ads are watched)
* Breaks the web UI, e.g. browser navigation, text selection, accessibility
* Not properly open - the license stipulates for what purposes you can use it (restricts uses such as downloading video)
* Not compatible with open source - can't ship as part of open source; so a pain for users as it requires a separate download.

Jeremy shows <a href="http://www.chromeexperiments.com/">Chrome Experiments</a> and <a href="http://icantbelieveitsnotflash.com">I Can't Believe It's Not Flash</a> (the site I made with @philhawksworth which should really be launched at some point. ahem.)

He walks through the history of Flash. He explains there was a time when they looked quite innovative, but it's become more closed systems and walled gardens, with silly license fees. So a young person who wants to get into the industry is required to pay 500 quid to get started with it.

Where does HTML5 fit in? A couple of weeks ago, <a href=http://whencaniuse.com">When Can I Use</a> launched, and the meta-message of that site - when you look at the complicated matrix of HTML feature support - can be interepreted as "Damn, HTML is complicated". This led some to say - why would I want to use HTML5 when I can get it up and running, cross-browser compatible - with Flash right away. So Jeremy's call to action is to take a few steps back and build some kller authoring tools that let us do similar things in Javascript.

In Q&A, @psd points out that Flash lets you make nice toys, but HTML5 lets you build something better than Flash, i.e. the data inside there.

<h3>Drupal 7 Update</h3>

<img src="http://posterous.com/getfile/files.posterous.com/mahemoff/7RYsNFTMvX6ojajfgYsFW6P1vNVRPfKVwXs8T0wIoW4cakRPZHXhErZvI5qP/photo.jpg" style="width:400px;">

Leisa Reichart explains the design work going on with Drupal 7. Where most open source (including Drupal) is done bottom-up, grassroots, stuff, there's an element of top-down design here. Leisa's talking about "open source design" (#d7ux), where she's spent around 85% of her time engaging the community to help with design, rather than just doing it herself. The community includes end-users, agencies whose customers are using the CMS, and also other designers and usability studies. (Reminds me of the message in the community session at OWF - don't just engage programmers, but also translators, designers, tech writers, etc.)

They set up a WordPress, yes WordPress, <a href="http://www.d7ux.org/">blog</a> to act as the community portal; because (a) Drupal takes too long to get a very nicely designed blog; (b) it sent out a message to the Drupal community and got them engaged.

She also shows a nice eye-tracking study, something you don't see much in open source land.
