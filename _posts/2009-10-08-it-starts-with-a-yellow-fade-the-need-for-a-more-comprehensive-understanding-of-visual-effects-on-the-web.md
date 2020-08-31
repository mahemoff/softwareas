---
id: 674
title: 'It starts with a Yellow Fade: The need for a more comprehensive understanding of visual effects on the web'
date: 2009-10-08T11:09:27+00:00
author: admin
layout: post
guid: http://softwareas.com/it-starts-with-a-yellow-fade-the-need-for-a-more-comprehensive-understanding-of-visual-effects-on-the-web
permalink: /it-starts-with-a-yellow-fade-the-need-for-a-more-comprehensive-understanding-of-visual-effects-on-the-web/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574478"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Ajax Patterns
  - Javascript
  - Patterns
  - Usability
  - Web
---
Around the time Ajax got coined, one of the already-known patterns was 37Signals' <a href="http://37signals.com/svn/archives/000558.php">Yellow Fade Effect</a>. As techniques were shared and <a href="http://script.aculo.us/ ">visual effects libraries</a> emerged, we began to see visual effects become commonplace on the web. I documented four of them in Ajax Design Patterns: <a href="http://ajaxpatterns.org/One-Second Spotlight">One-Second Spotlight</a>, <a href="http://ajaxpatterns.org/One-Second Mutation">One-Second Mutation</a>, <a href="http://ajaxpatterns.org/One-Second Motion">One-Second Motion</a>, <a href="http://ajaxpatterns.org/Highlight">Highlight</a>. (I wish I called them something else, e.g. "Spotlight Effect".) And all of these are around today, and even in the jQuery core which makes t
hem pretty darn accessible to any developer. It's as simple as $("message").fadeIn().

Where we are now, most developers are stuck with trial-and-error. In an ideal world, you'd have a SWAT team of UX experts to analyse each visual effect, test with users, and maybe they'd get it right, but most UI design in the real world and developers often just have to play around a bit and then move on to something else. So I think we could do with some simple guidelines, ideally based on empirical data, but even just based on pattern mining the web would be handy.

I'll give some examples of the kinds of problems I've faced as a developer building in visual effects:

* <strong>Choosing Visual Effect.</strong> I want to update some content that's just been received from the server. e.g. the football score changed. Do I show a yellow highlight, make it blink, make it vibrate, do nothing?
* <strong>Choosing Effect Parameters.</strong> I've decided to use a Slide Down effect. How longshould it last, i.e. the duration of time from not shown to show? Should it slide down at constant pace or accelerate and bounce at the bottom?
* <strong>Composing Effects</strong> I have a block of content with the user can edit. When switching it between edit and view modes, there are two simultaneous effects taking place - one thing is being hidden while the other is being shown. How do I handle those? Do I slide one up and when that's done, slide down the other? Do I fade one out and simultaneously fade one in? Do I immediately close one and transition in the other, or vice-versa? Many options come into play.

It should go without saying that there's no right answer for any of these problems. But instead of developers always working from first principles, I think there are some very useful guidelines and discussions that could be had around the design patterns involved. Maybe even leading to a high level effects library supporting those patterns. 