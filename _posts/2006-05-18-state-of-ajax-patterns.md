---
id: 300
title: State of Ajax Patterns
date: 2006-05-18T16:57:17+00:00
author: admin
layout: post
guid: http://www.softwareas.com/state-of-ajax-patterns
permalink: /state-of-ajax-patterns/
dsq_thread_id:
  - "377835663"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Book
  - Links
---
Here's what's going on with <a href="http://ajaxpatterns.org">AjaxPatterns.org</a> and the O'Reilly Ajax Design Patterns book. Many of you have mailed about this and many others asked at the conference, so this post is probably long overdue.

<h2>State of the Ajax Design Patterns Book</h2>

I finished the book a few months ago, and it's available <a href="">for sale now in Rough Cut form</a>. It was originally planned to be an "Animal" book, hence the bird dude depcited below, but because it has a fairly unique look and feel, it will now be part of the Theory In Practice series. So enjoy the birdie while it lasts.

<a href="http://img45.imageshack.us/img45/280/059610180501sclzzzzzzz9te.jpg"><img src="http://img45.imageshack.us/img45/6637/059610180501aa240sclzzzzzzz8vp.jpg"></a>

People at the Ajax Experience were asking about the book, conspicuously absent on the book stand, and the fact is it's taking a while to get into physical form for several reasons. Most importantly, I'm firmly committed to the idea that any physical pattern book needs to be highly visual - people should be able to flip through the book and see what the patterns mean in a blink. So there's a huge amount of diagrams and screenshots that the creative people at O'Reilly are working on, and I'm really happy with what they're outputting:

<img width="450" src="http://img212.imageshack.us/img212/3717/xdompn8zb.png"/>

The <a href="http://www.oreilly.com/catalog/ajaxdp/">electronic Rough Cut edition</a> contains my extremely "rough" diagrams, which serve as instructions for the illustrator and will eventually  make a nice historical manuscript.

<img width="450" src="http://i.imgur.com/XyeWW.jpg"/>
<!-- backup: http://img212.imageshack.us/img212/9518/inablink0265vy.png" -->

<h2>State of AjaxPatterns.org</h2>

I'm pulling it down so the book sells well.

But if I can be serious for a moment, the site will remain online with all content intact. It has always been, and remains Creative Commons, and if I had to choose between the wiki and the book, I'd take the wiki every time. It's staying online for the long haul, and I want to make it better than ever. These are my plans, let me know what you think:

* <b>Move to a faster, more reliable, host.</b> Dreamhost is great for hosting my blog, but DB-wise, is not up to the task of managing AjaxPatterns. I'm moving it to a Virtual Private Server (VPS) host, which is something I need for other projects anyway.
* <b>Open up for general editing.</b> Too many people came up to me at the conference and said "I have this pattern, what do you think?". What I think matters much less than what the Ajax community thinks, so I'd rather let people slap it on the wiki and let everyone judge it for themselves. I'd like to let people edit and enhance the patterns, provide examples, and so on. And add new kinds of content.
* Opening up the wiki obviously has huge risks involved, and there's been plenty of spambots already, capable of wiping out the wiki in a single execution. There's a strategy in place to help prevent, and also recover from, situations like this, but Mediawiki isn't fantastic here as there's no built-in Captcha support. I'm also sensitive to the charge that allowing open changes is a cynical way to make the content weaker, or more messy, and thus make the case stronger for buying the book. <b>So my plan is to hack the Mediawiki template so as to ensure the current version (the one that's there today) is always linked from each wiki page. How would you feel about that?</b>
* <b>Upgrade the standard theme</b>. You'll know why when you see it.
* <b>Add more content</b>. What Ajax info would you like to see? I've already begun work on a section for <a href="http://ajaxpatterns.org/Ajax_Tools">Ajax Tools</a>, this is exactly the kind of thing I'd like to open up for public editing. I also have plans for a whole new category of pattern, will get to it once all the other stuff's done.
* <b>Mashable patterns</b>. As I mentioned in my previous post, Bill Scott of Yahoo! is looking at a JSON/JSONP format for distributing the patterns. Once the format has been fleshed out, I'll set it up. The caveat will be that things might go a bit wrong sometimes with the wiki being openly editable (we'll need to do some cleansing to at least ensure no risk of XSS, though mediawiki is probably doing this anyway), but at least people will always get the latest info real time.
* <b>Release code for <a href="http://ajaxiify.com/run/">demos</a></b>.
* <b>???</b>
* Your thoughts and suggestions?