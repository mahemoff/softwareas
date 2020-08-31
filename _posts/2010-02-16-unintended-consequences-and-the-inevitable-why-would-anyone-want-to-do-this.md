---
id: 786
title: 'Unintended Consequences and the Inevitable &#8220;Why Would Anyone Want To Do This?&#8221;'
date: 2010-02-16T20:53:03+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=786
permalink: /unintended-consequences-and-the-inevitable-why-would-anyone-want-to-do-this/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "389986857"
categories:
  - SoftwareDev
tags:
  - IFrame
  - Javascript
  - Unintended Consequences
  - Web
---
I'm listening to <a href="http://www.bbc.co.uk/programmes/b00qj2nq">this excellent BBC podcast on Unintended Consequences of Mathematics</a>. 

<blockquote>
In his book The Mathematician's Apology (1941), the Cambridge mathematician GH Hardy expressed his reverence for pure maths, and celebrated its uselessness in the real world. Yet one of the branches of pure mathematics in which Hardy excelled was number theory, and it was this field which played a major role in the work of his younger colleague, Alan Turing, as he worked first to crack Nazi codes at Bletchley Park and then on one of the first computers.

Melvyn Bragg and guests explore the many surprising and completely unintended uses to which mathematical discoveries have been put.

These include:

The cubic equations which led, after 400 years, to the development of alternating current - and the electric chair.

The centuries-old work on games of chance which eventually contributed to the birth of population statistics.

The discovery of non-Euclidean geometry, which crucially provided an 'off-the-shelf' solution which helped Albert Einstein forge his theory of relativity.

The 17th-century theorem which became the basis for credit card encryption.
</blockquote>

The relevance to the topic of this blog should be clear.

Show me someone doing something <a href="http://ajaxian.com/archives/dojogfx-presentations-in-dojogfx">cool</a> or <a href="http://ajaxian.com/archives/javascript-jpeg-encoding">experimental</a> and I'll show you someone who sniffs, "Why would anyone want to do this?". The answer may be because it was fun, because they wanted to see if it was possible, or because they wanted to learn something. But whatever their primary reason, one thing's for sure: there will be unintended consequences. The examples above show it's happened in mathematics, and we've seen the same thing happen time and again in web development.

The rich interactivity we see today wouldn't have been possible if people hadn't been willing to fool around with the not-so-always-obvious features of web browsers. Take <a href="http://softwareas.com/cross-domain-communication-with-iframes">cross-domain iframe messaging</a>, for example. Not something people knew much about until a few years ago, when <a href="http://tagneto.blogspot.com/2006/06/cross-domain-frame-communication-with.html">James Burke</a> documented his experiments. A few years later, it's a fundamental technology in OpenSocial (which means iGoogle, the Yahoo! homepage, among many other sites), <a href="http://wiki.developers.facebook.com/index.php/Cross_Domain_Communication_Channel">Facebook's official Javascript client</a>,  and <a href="http://stackoverflow.com/questions/tagged/cross-domain+iframe">evidently</a> has much interest from elsewhere.

So next time you see some wit ask "Why would anyone ever need this?", just stay schtoom, sit back, and wait six months.