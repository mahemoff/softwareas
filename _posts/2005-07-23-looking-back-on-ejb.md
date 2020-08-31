---
id: 167
title: Looking Back on EJB
date: 2005-07-23T01:05:12+00:00
author: admin
layout: post
guid: http://www.softwareas.com/looking-back-on-ejb
permalink: /looking-back-on-ejb/
categories:
  - SoftwareDev
---
[Ted Neward](http://www.neward.net/ted/weblog/index.jsp?date=20050721#1122010458907) and [Floyd Marinescu](http://dynamicsemantics.blog-city.com/abriefhistoryofejb.htm) make some good points on EJB - is it really about distribution, impact of open-source, etc.

**The history of EJBs is a good demonstration of the "You Ain't Gonna Need It" principle applied to an entire industry.** At the time, it seemed like "this is what we'll do in the future, when we have the resources, the right app servers, the right IDEs, oh, and the need for it, so ... let's do it now instead! Hurray! Let's party like it's 2003!"

And then the backlash came, dipping its toes in the water by the time Rod Johnson's "J2EE Design and Development" came out,  and then outright contemptuous by the time Johnson's   "... Without EJB" call-to-arms appeared. Of course, lots of people snorted in the very face of EJB all along (serverside anyone?), but the mainstream Java attitude back then was "The EJB model is the way real software's done. Go back to your little <insert favourite scripting language> hacking if you feel otherwise."

So here we are, in that future, CPUs ten times as fast, etc., massive internet usage, and what's today's buzzword? "Lightweight"! To be fair, today's design paradigm is more about flexibility than low resource usage per se. As Dion Almaer said, [the container itself need not be lightweight](http://www.almaer.com/blog/archives/000482.html). Nor do the implementations. It's really about the framework being as transparent as possible. (A great HCI principle: "help me think about my job, not yours".)

EJBs will still be with us, but it's nice to see vendors like BEA  embrace Spring and related frameworks. Indeed, the whole dependency injection thing fits well with vendors - everyone needs an implementation after all.</insert>