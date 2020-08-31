---
id: 299
title: The Ajax Experience, May, 2006 (SF) Wrapup
date: 2006-05-16T23:48:56+00:00
author: admin
layout: post
guid: http://www.softwareas.com/the-ajax-experience-may-2006-sf-wrapup
permalink: /the-ajax-experience-may-2006-sf-wrapup/
dsq_thread_id:
  - "375572904"
categories:
  - Links
tags:
  - Ajax Experience
  - AjaxPatterns
  - Links
  - Web2.0
---
<img src="http://img110.imageshack.us/img110/1039/ajaxexperience125x1257qt.png" style="float: right; border-width: 3px; margin: 2px;" />Okay, for those watching my live blogging at <a href="http://ajaxian.com">Ajaxian</a>, you know I've just been to San Francisco for the <a href="http://theajaxexperience.com">Ajax Experience</a>. San Francisco is always a fine place to be for work or a conference, we're fortunate it turned out to be such an important place for our industry. I'm back home in London now and now it's time for a big braindump, where I'll do everything in my power to forget as many people and events as possible. Wish me luck!

<h2>Me, Me, Me: Ajax Design Principles and Patterns Talk</h2>

I'll get the plug out of the way, lest these links get buried in the rest of the text below. <b>You can find the slides to my talk here</b>:

* <a href="http://ajaxpatterns.org/ae2006/">Ajax Experience 2006: Mahemoff's Ajax Design Principles and Patterns Talk</a> 

Video and audio should be available at some point. (I'm sure that camera had a purpose.)

<b>If you saw my talk (or you end up catching the audio/video), I'D BE REALLY GRATEFUL FOR ANY FEEDBACK - positive or negative (other than stop shouting at me from your blog) - as comments in this blog or to michael@mahemoff.com. Thanks!</b>

The 90 minute talk covers:

<ul><li>How patterns help accelerate Ajax. You'll still make mistakes, but they're the ones workth making, not the ones others have already made.</li>
<li>Design principles for Ajax. I think people will perceive this as the dominant part of the talk.</li>
<li>Intro and overview of the patterns, including Walkthrough of the <a href="http://ajaxify.com/tutorial/">Ajax tutorial</a>.</li>
<li>Ajax Patterns Smackdown. An overview of competing patterns that is at once fun and informative, sharp and objective, fast and comparative, real and subjective. We take a single goal - e.g. "What format do I use to download data" - and we walk through two patterns that achieve it. At the end, I ask the audience who's using what, the results of which were interesting. I mostly stated them out loud for the sake of the recording, so I should be able to blog this informal poll when the audio's out.</li>
</li>
</ul>

I got all WebTwo-y and used <a href="http://www.meyerweb.com/eric/tools/s5/">s5</a> for the first time. Admittedly, I know a lot more CSS than last time I tried it, which sure helped, but I have to say it worked out really well. Resizing (which you have to do at conferences due to the projector - downscaled to 1024x768) was seamless.

I also appeared on the second night panel, where we had a range of memorable questions. (Video and audio also pending.) There's no live blog, and I won't pretend to remember what others said, but here's a couple of points I recall making.

Asked if Ajax means we're on the dawn of a new era of enlightenment (or something like that), I explained that if we are, it will take more than Ajax. As it happens, I do believe we are at such an age (though I wasn't going to go into it there), and I believe that Ajax is one brick in the wall. <b>Can  a UI technology cause such a profound change? It seems a bit cringeful</b>, but one point I did make, where I do think Ajax is quite profound, is <b>the ability to collaborate. As an application delivery platform (Douglas Crockford's term), we can tell 50 people a URL and using technologies like <a href="http://ajaxpatterns.org/Periodic_Refresh">Periodic Refresh (Polling)</a> or <a href="http://ajaxpatterns.org/HTTP_Streaming">HTTP Streaming (Comet)</a>, we can rely on most or all of them being able to collaborate together in real time. In contrast, these 50 people would end up fragmented in the desktop environment - they'd be using different OSs, different applications, and be subject to different security controls.</b>

We were also asked the obligatory (at this conference) and very important question on accessibility. <b>My response here was that we really need to reframe the question - people, in my view, are often overly negative about this. How about we take our new, poweful, abilities, and see how we can make things <i>even</i> better than we could in the past. I talked about customisation in my presentation - Ajax makes customisation a lot easier than in the past (compare <a href="http://netvibes.com">NetVibes</a> to <a href="http://excite.com">Excite</a>). Customisation is a seriously important aspect of accessibility. Ergo, in some areas at least, Ajax already gives us the ability to do better than before.</b> (Thankfully I didn't utter the word "Ergo". Crikey, I rarely even write it.)

<h2>Thanks</h2>

<b>The most important thing is to say thanks to Jay, Dion, Ben, Rochelle, Chris, Karsten, and everyone else involved in organising the conference and inviting me along.</b> You guys pulled off a great conference where people were able to get a lot out of it, no matter how Ajaxperienced. Thanks also to all the speakers for educating me on Ajax and certain others for educating me on SF :-).

<h2>Meeting People</h2>

It was cool to meet so many Ajax people, almost all for the first time in the flesh. Fellow <a href="http://ajaxian.com">Ajaxians</a> Dion and Ben, who work together so well in various talks and moderation sessions. It was also good to catch up with fellow Ajaxian Rob Sanheim, who I hope does a presentation next time on his Rails and PHP experiences.

<a href="http://www.ashleyit.com/blogs/brentashley/">Brent Ashley</a>, resplendent in Ajax (football club) tracksuit and cap, with custom-made Javascript-style cleaning ad T-shirt, has a fantastic attitude to the whole movement and offered many insights into its evolution. Remember, this guy was doing remoting in the last century. You know the Java-inspired joke about "Must have 6 years Ajax experience"? Brent and I discussed how the existence of people like him (and probably others at the conference) kind of invalidates it :-).  Brent deserves a special mention as he's the guy who originally promoted Ajax Patterns to the initial Ajax Summit (which oddly enough wasn't mentioned at the conference) and in his blog.

As just blogged, <a href="http://www.softwareas.com/so-jesse-is-ajax-a-pattern">I briefly met the "father of Ajax", Jesse James Garrett</a>. His talk was probably interesting to many, but in my case I've heard various elements before, so less new info for me. (Indeed I've transcribed and blogged about a couple of podcasts he's appeared on, so I know way too much about this story). One especially cool thing was how he very explicitly made the point, wich will probably be ignored by all the dogmatic pedants out there, <B>that Ajax is not just XMLHttpRequest</b>. These people really should be relying on community conventions to work out what a name means (language evolves BTW, and words can only mean whatever people collectively use them to mean). However, if they retentively insist on idolising the Ajax Guru, at least they might consider listening to what he says in talks like this. It reminds me of the scene in Fight Club where "Jack" (Ed Norton) admonishes the crew - "This guy has a name. His name is Robert Pawson". The sentiment is lost on the crew, who simply want to be told what to do from their Fight Club Guru and start chanting "His name is Robert Pawson. His name is Robert Pawson." My point? If you find it so difficult to think for yourself that you must have a Guru, at least follow what he says. (If I seem "emotionally committed" to this point, read the Wikipedia Discussion on <a href="http://en.wikipedia.org/wiki/Talk:Ajax_%28programming%29">Ajax</a>, where you'll discover any number of <strike>Ajax</strike>A.J.A.X. authorities who revel in equating the concept with "Here's what we can do with XMLHttpRequest".

I also met <b>The Grandmother of Ajax</b>. For real. I'm referring to Jesse James Garrett's mum, who took a few pics of her son at the end (and presumably during the talk). The "Grandmother of Ajax" label comes from Brent Ashley, who uses colourful language to describe his own role, and that of Adam Bosworth, relative to JJG's "father".

I was looking forward to <a href="http://looksgoodworkswell.blogspot.com/">Bill Scott</a>'s talk on <a href="http://developer.yahoo.com/yui/">Yahoo's usability patterns effort</a> all along and he didn't disappoint (<a href="http://ajaxian.com/archives/ajax-experience-day-3-bill-scott-on-ajax-design-patterns-and-principles">My notes on Bill's talk</a>). He gave plenty of examples and I especially liked his screencasts. I learned a few things about Yahoo's approach and also some interesting ways to present pattern material. Whereas I separated out principles from patterns, Bill explained a principle and outlined several related patterns. As Bill mentioned in his talk, he's spearheading an effort to help people mashup the patterns. I've already demo'd a couple of examples of this, using only the AjaxPatterns: <a href="http://www.ajaxify.com/run/reader/logging/clientTest/realService/">The AjaxPatterns Reader</a> and the <a href="http://www.ajaxify.com/run/portal/drilldown/syncLinks/">AjaxPatterns Portal Demo</a>. Bill's plan is for all of us (Yahoo, AjaxPatterns, and other collections) to expose pattern data as JSON (most likely, JSON-P), so people can combine them how they please. Writing some JS code, you'll be able to say "Give me the HTML for the solution of Cross-Domain Proxy".

<a href="http://alex.dojotoolkit.org/">Alex Russell</a> and <a href="http://www.develop.com/">Stuart Halloway</a> were two of the speakers I met, both of whom have extremely deep knowledge about this stuff and know how to convey it. In both cases, doing plenty of coding on the fly. I'm more pumped than ever to get into Dojo. I only wish, like others have said, they'd have more doco, as the lack thereof has killed many a worthy open-source project. Already, I think Prototype and Scriptaculous are kicking Dojo's butt, in terms of developer numbers, and the documentation for them (esp Prototype) isn't especially abundant anyway. Doco isn't just important for developers, but also other library manufacturers. Mochikit, for example, takes advantage of Dojo's packaging structure, and with the right doco in place targeting toolkit authors, the packaging structure has a great chance of becoming a de facto industry standard. This would be a good thing for everyone - the greatest benefit is faster downloads. (In his talk, Alex explained how the basic bootstrapping requires just 5kb of compressed Javascript, so any library could feasibly benefit from this approach, even Prototype/Scriptaculous!).

I met many others, including <a href="http://blogs.ebusiness-apps.com/andre/">Andre Charland</a> of E-Business, with whom I've communicated with several times via our blogs, and Rob Gonda of iChameleon. Andre was, AFAICT, the only person who attended both conferences I was at - The Ajax Experience and <a href="http://www.socialtext.net/dcamp">DCamp</a> (another post about DCamp at some point).

I also met many other attendees who I won't mention here. It was especially cool to meet people from one website which I used in some of the examples for AjaxPatterns. I distinctly remembered some of the things in their source code (trust me, it's memorable), where it was cool to get the background on.

Some people I never got a chance to meet, hopefully next time. Eric Pascarello and Douglas Crockford, for instance.

And I promised I'd forget to mention lots of people too, so I'd better leave it here as I'd hate to disappoint.

<h2>Main Themes</h2>

Every conference has special, unplanned, themes.

Just about every session mentioned<b> the importance of using libraries</b>. I blogged earlier on that there are now <a href="http://softwareas.com/134-ajax-frameworks-and-counting">134 libraries and frameworks</a> out there. A straw poll in the panel indicated many people are still rolling their own, so the message was a worthy one.

Every panel had the obligatory question on Ajax and <b>accessibility</b>. I already explained my own attitude above. Bill Scott mentioned that Yahoo! has a specialist looking at all their stuff from an accessibility point of view, and I think he also mentioned there's a Flash specialist taking that into account as well.

With a keynote from Brendan Eich and a panel with himself and Laurel of IE present, <b>browser and JS enhancements were a big part of Day 3. Seeing Brendan talk about what's coming with JS 2.0, there's something God-like going on. It's like this guy's defining your new powers, your new constraints, the laws of gravity that you'll be spending every day living under when you develop web apps. That's the nature of web development - you can play with back-end environments all you want, but at the end of the day, you're bound to whatever the people at the front of the room decide to give you. And then you sit back and go "it was all a dream" as it suddenly occurs that you're stuck supporting the current batch of browsers for the next few years, and who knows if IE and others will implement half of this stuff anyway.</b> It was cool to see Stuart Halloway, Alex Russell, and Douglas Crockford up there on the panel with Brendan and Laurel - they provided a good counterpoint as champions for the developers and the tool makers.

Speaking of Douglas Crockford, a few people mentioned his JSONRequest spec, which <a href="http://ajaxian.com/archives/jsonrequest-proposal-for-cross-domain-browser-service">I blogged a couple of months back on Ajaxian</a>. This is gaining momentum - Brendan is bullish and mentioned that it's trivial to implement - though Laurel (IE) didn't say too much. Hey, even if it's only in Firefox, we're going to see some cool apps come out of it. The basic idea is a safe cross-domain caller (no cookie transfer).

I'd expected Comet to be a big buzzword at this conference, but it seems most people are still getting to grips with Ajax 1.0. I did, however, come across a new term for Comet/Streaming/Polling- "Reverse Ajax", which I believe DWR uses among others. Do I like the term? No, because I don't like the term Ajax to describe just remoting. But I think we're going to be stuck with it.