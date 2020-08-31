---
id: 173
title: Spying on Users With XMLHttpRequest
date: 2005-08-10T18:15:19+00:00
author: admin
layout: post
guid: http://www.softwareas.com/spying-on-users-with-xmlhttprequest
permalink: /spying-on-users-with-xmlhttprequest/
dsq_thread_id:
  - "375572369"
  - "375572369"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Links
  - XMLHttpRequest
---
Earl Castledine points out the allegedly dark side of [XMLHttpRequest: spying on users](http://www.devx.com/webdev/Article/28861) ([thanks Ajaxian](http://www.ajaxian.com/archives/2005/08/fud_using_the_x.html)). **It seems that this capability will cause it to "likely fall from grace"!** (I mentioned the issue a little while ago regarding the [Heartbeat pattern](http://www.softwareas.com/heartbeat-pattern-supporting-library)). 

Two examples are given in the new article:

> you write an e-mail to Apple support that says: "I just bought a brand new iPod. I dropped it down a set of stairs. It stopped working." You then decide to delete the second sentence to help your cause. TOO LATE! If the site uses AJAX, your response may already have been zapped to the complaint desk in the sky!

I agree this could actually happen. The [live chat/wiki demo](http://ajaxify.com/wiki/), for example, is based on a [Fat Client](http://ajaxpatterns.org/Fat_Client) model, where the browser essentially runs a full app and periodically synchronises with the server, during which time intermediate info is logged. HOWEVER, even if the Apple support guy had access to the data, and felt like poring through every partial text at 5-second intervals, and the user was unlucky enough to have submitted the guilty message, I doubt it would hold up because you can sync all you like, but the user can't be held responsible for what they wrote until they've acknowledged the message is done. This legal motivation is one reason why you'll always see [Explicit Submission](http://ajaxpatterns.org/Explicit_Submission) in some Ajax apps, even though [Submission Throttling](http://ajaxpatterns.org/Submission_Throttling) renders it unnecessary from a technical perspective.

The second example:

> Or --- a little more malevolently --- consider this: most people have one or two username/password combinations that they use for all of their "unimportant" sites such as news sites, blogs, and forums. They probably also have a few reserved for use on more sensitive sites --- banking, Web mail and work accounts. It's a very common and easy mistake to begin typing incorrect login details for a given page. Force of habit is responsible, but people usually realize what they've done before hitting the submit button.

I suppose it's possible once again, but since there's a concrete example to go by, I'm going to take this one literally too. The problem here could just as easily occur in a traditional app - I'm sure users frequently submit the wrong user/password too. That would actually be more dangerous than just periodically capturing what the user's typing, because how do you know when they're finished. Even when someone does capture such information, they  still have to start guessing where it applies. Also, if users only have one or two combinations, they're pretty likely to type in the same password anyway, ne? So what's the devious webmaster getting at that they couldn't get at before?

The thing is, **you could have captured all this information before**. Here's how you do it the new way, with XMLHttpRequest:

* Every few seconds, post the current browser state to the server.

Here's how you do it with standard forms:

* Every few seconds, push the state onto an array.
* When the user eventually submits a form, upload a string representation the array.  Note both of the examples above involve submitting a form eventually, and note that even an external hyperlink can easily be scripted to force a form submission. It's a little more work, but it was always feasible.

Admittedly, one difference is that **XMLHttpRequest provides some cover for malicious activity, because periodic submission is standard practice, whereas periodically submitting history is just a little suspect**.

While this sort of stuff is mostly FUD, **Ajax does bring out the common tension between usability, security, and privacy.** The [Heartbeat](http://ajaxpatterns.org/Heartbeat) pattern, for instance, involves monitoring page events to see if the user's active. Definite security benefit, definite benefit for resource conservation, but also a definite increase of personal monitoring. 

In any event, users need to be aware the security model of the web is that **whatever basic actions they perform on the page are open to the operator of that site**. XMLHttpRequest may play a small part, but it won't be falling from grace anytime soon.
