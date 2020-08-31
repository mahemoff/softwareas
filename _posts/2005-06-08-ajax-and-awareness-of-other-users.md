---
id: 142
title: Ajax and Awareness of Other Users
date: 2005-06-08T04:45:33+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-and-awareness-of-other-users
permalink: /ajax-and-awareness-of-other-users/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
categories:
  - HumansAndTech
  - Links
---
A few Ajax UI idioms are emerging, e.g. progress icon while waiting for server response. But I haven't yet seen anything for awareness of other users. I was just playing with the [magnetic poetry demo](http://www.broken-notebook.com/magnetic/) (via [Ajaxian](http://www.ajaxian.com/archives/2005/06/degradable_ajax.html). The pieces started moving on their own volition, which I assumed was, uh, due to magnetism. It turns out it was someone else, but there was no way to know that. I'm not knocking the demo here, which after all is very cool and in fact every ajax wiki/chat app I've seen does the same. I'm suggesting that it would be nice if these **multi-user apps had a way to express information about others**, respecting privacy of course.

Some of these things are already done on websites like messaging boards, which I assume use the last time of request to see if the user is "online". With Ajax, you can be a lot more certain if the user is "online":

* You can use a heartbeat mechanism to keep checking the application is alive and well in the browser.
* You can monitor user activity to detect when a user has gone idle.

Short of strapping on eye-trackers and performing a PET scan, that's about as good as it gets, even on the desktop.

So, armed with this kind of information, you could do the sort of things you see on desktop applications or collaborative websites:

* **Show how many users, and possibly a list of those logged on, if their profile wants it. "last seen" time, etc.**
* **Use different cursors for different users**
* **Use a modified "yellow fading technique" to show when *someone else* has changed something. Maybe it should be a reverse-fade to pretend that it's being squeezed out of the server, as opposed to being sucked in (which is how I see the fading technique work).**
* **When all's said and done, it all comes down to one thing: Avatars. Well, not really. I just thought "avatars" would be cool to mention here.**

I'm sure there's lots more of these waiting to be discovered.

As I've mentioned before, intranets are the killer app for Ajax, and there are scores of opportunities for collaborative Ajax systems in the enterprise.