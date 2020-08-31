---
id: 1146
title: 'Live Blogging at QCon HTML5 Track: Dave Recordon on HTML5 at Facebook'
date: 2011-03-11T17:27:59+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1146
permalink: /live-blogging-at-qcon-html5-track-dave-recordon-on-html5-at-facebook/
dsq_thread_id:
  - "375201238"
categories:
  - SoftwareDev
tags:
  - Conference
  - html5
  - QCon11
---
<img src="http://desmond.yfrog.com/Himg612/scaled.php?tn=0&server=612&filename=iakdb.jpg&xsize=640&ysize=640" />

I did my talk on Single Page Apps and  this morning at QCon today on Single Page Apps and HTML5 History. The demo raised a number of interesting design principles/patterns which I'll cover in a later post...but for now, I'm going to post a few live blogs from sessions here. [Update - <a href="http://alblue.bandlem.com/2011/03/qcon-day-3.html">AlBlue's posted a summary of talk.</a>]

First up, Dave Recordon explains how HTML5 is being used at Facebook.

Dave Recordon explains he works with Facebook's developers to promote web standards and HTML. What is the promise of HTML5?

He begins by asking the obligatory, "What is HTML5"? His definition agrees with mine - not just a spec, but the technologies that let developers make awesome apps, and a <a href="http://softwareas.com/html5-is-a-brand">brand</a> that developers can rally around.

<h3>HTML5 at Facebook - Today</h3>

While some say HTML5 isn't ready till 2025, Facebook wrote on their blog about <a href="">"Using HTML5 Today"</a>, a look at a bunch of things they're already working on:

<h4>History.</h4>

Facebook has a framework called Big Pipe which loads the overall page structure, and then a second structure called QuickLink which overloads links to reload just parts of the page. This led to ugly URLs, with fragment IDs e.g. http://www.facebook.com/profile.php?id=24400320#!pages/Engadget/5738237369, and history gets them around that.

Recently, they created a new photo app which involves photo sharing and lightboxen to show the photos.

window.history.pushState("http://facebook.com/full/url/to/photo", null, "http://facebook.com/photo.php?fbid=123456678 ....");

<h4>Web Video</h4>

Dave explains that Facebook hosts a lot of web video, and there's no clear way to deal with it rigt now because of codecs...but, he says, it's fair to say most people today would go with H.264 or WebM. Today, H.264 is Safari and IE, WebM on Chrome, Firefox, IE, and Opera. This difference, as well as DRM, is one of the reasons why people are still choosing Flash for video.

Dave bigs up video.js as a way of dealing with the complexity, and says they're still using Flash for the most part, with the following advice:

* Use your own Flash player if you're already built one.
* Use the same size poster image, raw video file, and Flash player.
* iOS devices only support H.264.
* Storage for double (or even triple) encode become costly, quickly.

<h4>Sprites and Gaming</h4>

They analysed the requirements for gaming. 10fps gets you minimum interaction for a game, but really you need to focus on 30+ frames per second, so this is where they focused. How many sprites do you need for a game? 5 sprites for a simple baord game, leading up to 100 for a 2D game (that's the scope they focused on).  They found the modern browsers can deal with the requirements well, e.g. with WbGL, Chrome 11 can handle 4000+ sprires.

He walks through various options for showing a spaceship. Just an image? A sprite? But if so, a div with a background image or a mask over the big sprite sheet image. They've done research to this end.

See http://github.com/facebook/jsgamebench

<h4>Mobile</h4>

Hundreds of millions of people access Facebook from their phones, so Facebook's looking into how HTML5 can help here. Which platforms do you need to target?

* Features phone
* iPhone
* Android
* BlackBerry
* Palm Pre
* Windows Phone 7

Dave says that even for Facebook, let alone a startup, it's hard to keep up with all these devices. The wurfl project maps devices to capabilities (e.g. does it support JS? what screen resolutions?), which Facebook is using and feeding data back into it.

The popularity of WebKit makes it easy to target multiple devices at once, and this is apparent in the way PhoneGap works to let you target multiple devices in the one go.

<h4>Assorted Questions</h4>

<strong>Dealing with IE6?</strong>

Decided not to support chat on IE6, but generally try to support older browsers as well, simply by way of the numbers.