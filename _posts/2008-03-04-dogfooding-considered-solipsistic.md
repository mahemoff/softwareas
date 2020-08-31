---
id: 433
title: Dogfooding considered solipsistic
date: 2008-03-04T18:04:32+00:00
author: admin
layout: post
guid: http://softwareas.com/dogfooding-considered-solipsistic
permalink: /dogfooding-considered-solipsistic/
dsq_thread_id:
  - "375573622"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Dogfood
  - Nitobi
  - Usability
  - Usability Testing
---
<img src="http://img175.imageshack.us/img175/8536/dogadsi4.png">

<a href="http://www.codinghorror.com/blog/archives/001066.html">Jeff Attwood encourages developers to eat their own dogfood</a>:

<blockquote>
I've found that much of the best software is the best because the programmers are the users, too. It is UsWare.

It behooves software developers to understand users, to walk a mile in their shoes. If we can bridge the gap between users and ourselves-- even if only a little-- we start slowly converting our mediocre ThemWare into vastly superior UsWare. To really care about the software you're writing, you have to become a user, at least in spirit. 
</blockquote>

This is good if you're writing an IDE, not so good if you're writing a word processor and actually kind of plain wrong if you're writing a medical or trading app where developers lack the knowledge and experience of typical users. <a href="http://www.codinghorror.com/blog/archives/000287.html">As Jeff himself has noted elsewhere</a>, "If the application you're writing isn't intended for expert users, having the developers dogfood it won't necessarily buy you much, because developers are highly unrepresentative of typical users. Beyond fixing critical bugs, it could even hurt the application: developers tend to add advanced, complicated features that are useful to them." 

At this point, I'm supposed to launch into a tirade about how <a href="www.amazon.com/Inmates-Are-Running-Asylum/dp/0672316498">the inmates are running the asylum</a>, but I actually think that's a pretty condescending attitude, albeit one that has includes some arguments to be aware of. It's also somewhat of a self-fulfilling prophecy. Professional software developers have an important role to play in working towards usability, especially in the very real situation where usability professionals are simply not available.

How do you improve usability when you can't eat your own dogfood? The solution is to become an anthopologist and watch <i>actual users</i> eat your dogfood. There are a lot of variants of this:

* <strong>Paper prototyping.</strong> For early design feedback. Incidentally, paper prototyping is a lot more than just lo-fi, hand-drawn, sketches. "Real" paper prototypes are interactive, like a board game, with a little real-time prodding from the researcher and possibly an assistant domain expert.
* <strong>Contextual analysis.</strong> This goes by several names, but the idea is to sit in the real-world environment of users and see how they interact with the system, as well as other systems, other people, and the general environment. The only problem with this approach is that you can't do it with an in-progress system; it either has to be the old, extant, system, or the new, almost-complete, system.
* <strong>Interviews and walkthroughs.</strong> The user sits in a "usability lab" (but probably just an office) and runs a test version of the system, discussing it with the researcher. It may also be that there's no system involved, just a qualitative discussion.
* <strong>Automated monitoring.</strong> A fan favourite of privacy advocates everywhere ;) - so please inform users what you're monitoring, let them opt out, etc. This involves logging and monitoring of user actions for later monitoring. Thanks to the magic of Ajax, there are now some very powerful tools that will track all activity in the browser and play it back for later analysis. For example, <a href="http://about.stompernet.com/scrutinizer">Scrutinizer</a>, written by the talented <a href="http://www.nitobi.com/">Nitobi</a> team. Scrutinizer is cool because it actually blurs everywhere outside the mouse pointer area, so is an okay approximation for a full-blown eye tracking system. I haven't heard of biological testing - especially PET scans - but with growing inteterest in <a href="en.wikipedia.org/wiki/Neuroeconomics">Neuroeconomics</a>, I'm sure it's coming.

A related problem of dogfooding is that software developers tend to enjoy writing systems for themselves, i.e. those where they really will be eating their own dogfood. This is why we have: a proliferation of IDEs and clones of the veritable Unix "make" utility; quite an unreasonable number of applications about Klingon and juggling; but far fewer about quilt making and the art of kite surfing.

All this goes a long way to explaining why the greatest usability is often seen in software related products. I rate IntelliJ Idea, Firebug, and the general Unix philosophy among the best exemplars of software usability ever created, in any domain. Mainstream business and scientific applications will never be as good as those applications through the application of dogfooding.

<object width="425" height="344"><param name="movie" value="http://www.youtube.com/v/GO4GCHJRhrk&hl=en&fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/GO4GCHJRhrk&hl=en&fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="344"></embed></object></div>