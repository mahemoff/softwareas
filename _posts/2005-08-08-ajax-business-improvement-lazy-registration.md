---
id: 172
title: 'Ajax Business Improvement: Lazy Registration'
date: 2005-08-08T21:56:26+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-business-improvement-lazy-registration
permalink: /ajax-business-improvement-lazy-registration/
dsq_thread_id:
  - "384547955"
  - "384547955"
categories:
  - HumansAndTech
  - SoftwareDev
---
**Lazy registration is a killer app for Ajax usage in business.** Tim Haines has a contest going on to [improve a business model with Ajax](http://ims.co.nz/blog/archive/2005/08/02/897.aspx) ([right on, Rick Strahl](http://west-wind.com/weblog/posts/2725.aspx)). The contest is about an online ecommerce site - I can do better than a suggestion ... I've got a working prototype for this one and an explanation at http://ajaxpatterns.org/Lazy_Registration. (Lazy registration sits nicely with a lazyweb contest of this nature :-) .

The idea is not mine at all actually, it's been done for a long time by sites like Amazon, and [Chris Were, AKA Tahpot](http://tahpot.blogspot.com/2005/06/lazy-registration-with-ajax.html) had the insight to see what Ajax can hold for it.

The demo is online at:
[http://ajaxify.com/run/shop/](http://ajaxify.com/run/shop/).
Go and see how easy it is to register when it all happens on the page. (It's all cookie-based, your account won't really be persisted). A small website like HandyShop (that in the contest) gets killed by Amazon because users don't want to go through *another* registration process. **Ajax makes registration light work, thus dropping a massive barrier for ecommerce sites.**

And yes, it's just a demo. Some things could be improved.

Quick summary:

* New users get an ID immediately.
* All registration occurs inside an independent [Portlet](http://ajaxpatterns.org/Portlet). There's no 10-minute distraction caused by page reloads and email verifications, all those things which traditionally kill an ecommerce site's chances of a user buying something. The registration is completely parallel to the main site usage, the user can gradually flip between the two.
* Gradually accumulate info, whether officially registered or not. In the demo:
 * You can enter your email to have the shopping cart mailed to you. Once you do this, the email is already known and will always appear in the profile. You've just dropped a major barrier to the registration, as the user has provided their login ID (the email address) in exchange for a service.
  * Your preferences are monitored and shown in your profile. You can override it and set them manually.

Each of the Ajax Patterns has a story to provide a concrete illustration of how they can be used. Here's the story for Lazy Registration:

> It's Saturday afternoon, and Stuart is busy planning the evening's activities. He visits a band listings website, where he clicks on a map to zoom into his local area. Even though he's never visited the site before, a profile is already being constructed, which he can see on the top of the site. At this stage, the profile guesses at his location based on his actions so far. As he browses some of the jazz bands, the profile starts to show an increasing preference for jazz bands, and some of the ads reflect that. Since the jazz thing is a one-off idea, he goes in to his profile and tweaks some of those genre preferences, but leaves the location alone as that was correctly guessed. Finally, he decides to make a booking, at which point he establishes a password for future access to the same profile and also his address, which is posted back to the profile.

I'm tempted run my own competition to see if anyone can tell me how this **can't** be a good thing for businesses.

XMLHttpRequest gets most of its groovy factor from the fact that the user doesn't see an entire page reload. **But there's another big benefit people often overlook: state remains on the page.** So you can really have entire parallel conversations going on within the same page, and no need to post twenty variables in hidden fields just because one tiny query is required.

Actually, there are plenty more ideas possible and many of the [ajaxpatterns.org](http://ajaxpatterns.org) stories, like the one above, are intended to give a glimpse as to what's possible. So while most of the demos at ajaxify.com are of the [â€˜Hey look what I can doâ€™](http://west-wind.com/weblog/posts/2725.aspx) variety, the corresponding patterns show how Ajax can go well beyond the hype.

<b>Update:</b> Just an hour after posting this, I saw <a href="http://www.ajaxian.com/archives/2005/08/palmsphere_mark.html">Ajaxian</a> has linked to the <a href="http://palmsphere.com/store/home">Palmosphere</a> website, which actually performs a kind of lazy registration, letting you add favourites before logging in. I'll go add the example to the pattern write-up shortly.