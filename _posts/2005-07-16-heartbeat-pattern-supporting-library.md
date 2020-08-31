---
id: 164
title: 'Heartbeat Ajax Pattern &#8211; A Code Example'
date: 2005-07-16T02:36:08+00:00
author: admin
layout: post
guid: http://www.softwareas.com/heartbeat-pattern-supporting-library
permalink: /heartbeat-pattern-supporting-library/
dsq_thread_id:
  - "375353299"
  - "375353299"
categories:
  - HumansAndTech
  - SoftwareDev
---
[Erik Pascarello](http://radio.javaranch.com/pascarello/2005/07/05/1120592884938.html) (ahoy hoy [Ajaxian](http://www.ajaxian.com/archives/2005/07/update_users_se.html)) has created a library to track the user's session. This is a nice implementation of an [Ajaxian Heartbeat](http://www.ajaxpatterns.org/Heartbeat).

**One of the biggest frustrations with traditional web applications is that users get timed out.** With Ajax, you have a few more options:

* **Keep sending requests to the server,** so the server knows the browser page is still present - the user hasn't quit or loaded a new URL, so there's at least a chance they'll return.
* As with Erik's implementation, **explicitly ask the user if they want to quit close to timeout**.
* **Trace the user's browser's activity, to check if they're actively working with the application.** Actually, Neil Brewer of Trinsoft, alerted me, after listening to the [Ajax podcast](http://www.softwareas.com/ajax-podcast), that this is a potential negative of Ajax, the privacy concern. And ["The Fonz"](http://www.mrspeaker.webeisteddfod.com/2005/04/17/the-fonz-and-ajax/) makes exactly this point. Actually, the whole title is "The Fonz uses XmlHttpRequest and AJAX to spy on you.". Isn't that cool? The Fonz delivering community service announcements in 2005, warning against the evils of XMLHttpRequest :-) ). This is certainly an issue, although to be fair, you could do the same thing without XMLHttpRequest, by just buffering it up user activity and uploading it on the next POST. Plugins will probably help here, like more end-user-oriented versions of the [XMLHttpRequest debugger](http://blog.monstuff.com/archives/000252.html). In any event, for heartbeats, the solution's simple: all you have to do is track user events in the browser, but only send a basic heartbeat if anything has actually happened - no more need be sent.

OK, so heartbeat's about ending user frustration? A lot more than that actually. **Think "Pessimistic Locking", a very useful pattern in the enterprise that's troublesome on the web. It has its good and bad sides relative to optimsitic locking, but on the web, the bad sides are exacerbated by the timeout issue.** How do you know if the lock holder is actually working hard in the browser on the locked artifact, or if they've quit the browser, thrown the computer out the window, and gone fishing? Traditionally, you couldn't tell the difference. With Ajax, you can make a much more informed guess.