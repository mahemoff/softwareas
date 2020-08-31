---
id: 1272
title: WordPress Comments Out, Disqus Comments In
date: 2011-08-04T09:56:00+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1272
permalink: /wordpress-comments-out-disqus-comments-in/
dsq_thread_id:
  - "376899633"
categories:
  - General
tags:
  - Comments
  - Disqus
  - Navel-Gazing
---
<a href="http://www.cloudave.com/10359/i%E2%80%99m-sticking-with-disqus-here%E2%80%99s-why/"><img src="http://www.cloudave.com/wordpress/wp-content/uploads/2011/03/6d902ab26c78a181312897a0a3d4bcaa2.jpg" /></a>

### A New Comment Experience

Continuing the navel-gazing theme, I've finally migrated 6 glorious years of your WordPress comments to the cloud. Oh wait, they're already in the cloud. But I've migrated them to someone else's cloud. This blog being about software and the like, wanted to reflect on the motivation and process to move comments to Disqus ...

I primarily decided to do this because it's incredibly hard to "follow the conversation", despite social media pundits telling us that's exactly what we should be doing. Technorati is effectively no longer. Other systems which try to alert you to new links lag and miss many. Spam is not the only cause; the proliferation of URL shorteners is another factor. I'm hopeful Disqus will do a better job. So far, so good.

Furthermore, Disqus lets commenters post via their online identity - Twitter, etc - and also show posts or comments though those media. As a user commenting elsewhere, I've found it vastly preferable to the old school "enter your name, email, url, AGAIN".

To be fair, I'm still not crazy on the user experience of dynamic ("Ajax") comments, something I experimented with myself in <a href="http://softwareas.com/scrumptious-conversations-about-websites-and-other-resources">Scrumptious</a>. There are other comment widgets around (UserKit, Facebook, Google Friend Connect which one could assume will be replaced at some point by a G+ equivalent), but I like Disqus for its flexibility - not tied to any one user/social platform - and user experience. They've done a great job in both desktop and mobile browsers of making the dynamic comment experience pretty smooth.

I heard a podcast where someone was complaining about people "giving up their comments" to third parties. When challenged to say if he's ever "used" those comments, he was silent. I don't expect to do anything with comments other than display them. The only risk would be Disqus shutting down, and they provide an XML backup dump. I couldn't see if anyone has actually scripted the migration back to WordPress, but we can be certain it will happen in a jiffy in the unlikely event Disqus was to shut down.

### Installation

Installation was pretty simple, took around 15 minutes. I did have to sign up to Akismet and tell Disqus my key, which fine, but a surprise as I thought spam prevent was one of Disqus's core competencies.

I also appreciate that I get a mail for each comment, which I can reply to, or reply with "Delete" if it's unwanted. (It's only sent me one false negative spam in 48 hours.)

The WordPress plugin is nice. It works (not a foregone conclusion in the WordPress plugin universe), it has a nice UI, and it integrates with Comments as a complete replacement.

The migration itself actually took about 12 hours and led me to be slightly concerned. We're so used to instant gratification, but for a free service, I think this is fine. I just wish they'd made it more clear about average times to save me trawling through the forums to discover it's normal.

For whatever reason, the resulting text was way small. So I tweaked the WordPress Cutline theme's custom.css for a larger font:

[css]
#disqus_thread { font-size: 1.4em; }
[/css]