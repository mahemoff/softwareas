---
id: 355
title: 'Phobos &#8211; Server-Side JS Redux'
date: 2006-11-11T20:45:18+00:00
author: admin
layout: post
guid: http://www.softwareas.com/phobos-server-side-js-redux
permalink: /phobos-server-side-js-redux/
dsq_thread_id:
  - "375418024"
categories:
  - SoftwareDev
tags:
  - Ajaxian
  - Java
  - Javascript
  - Links
  - Phobos
  - Rails
  - Ruby
  - Server-Side Javascript
---
<img src="http://img385.imageshack.us/img385/6316/phobosbo0.png" width="200" height="200">

<a href="http://ajaxian.com/archives/phobos-does-sun-have-a-good-thing-under-its-nose#comments">On Ajaxian</a>, Dion points to Sun's <a href="https://phobos.dev.java.net/">Phobos project</a>, an attempt to build a new platform for server-side Javascript. Phobos came out <a href="http://blogs.sun.com/theaquarium/entry/project_phobos_is_live">six months ago</a>, around the time of the May Ajax Experience.

No-one has taken server-side Javascript seriously since it died a premature death in the mid-90s. But there is great potential...

* Server-side Javascript would allow for code sharing between browser and server. The most obvious application being validation code, but since no-one really bothers with server-side Javascript, there are probably many other patterns as well. One pattern I came up with a while ago is <a href="http://ajaxpatterns.org/Dual-Side_Templating">Dual-Side Templating</a>, where you have the same parametized HTML template on both the server (for initial page load) and the browser (for subsequent additions to the page). I implemented the server templating in Ruby, but it would have been a lot easier if the server was running JS. That's just one example.
* Server-side Javascript would keep us Ajax types more sane. Right now, an Ajax developer has to constantly flip between JS and [insert favourite server-side language here]. True, you always have to flip over to other "languages" too, viz. HTML, CSS, SQL; but there's always a special place in the programmer's head for the core language of the day. With Ajax, you have two such languages. If those  languages are quite similar (e.g. Javascript and PHP), it gets frustrating because of all the subtle differences (<tt>new Array()</tt> versus <tt>array()</tt>). If they're different (Javascript and Ruby), you're trapped in a Whirf-Brock disconnect, constantly flipping between two different worldviews. <em>Slight</em> exaggeration as it's certainly do-able, but it would be a lot easier if programming in one main language.
* Server-side Javascript would pose less of an issue for IDEs. With new improved Javascript, IDEs are being forced to support Javascript in order to keep up. It's far more important than supporting SQL etc; so basically, IDEs now have to provide solid support for at least two serious languages...it would be easier if it was only one.

Now a framework like Phobos has much to offer the world compared to the server-side Javascript of the mid-90s:

* Phobos is apparently inspired by new frameworks such as Rails. With the right libraries and improved patterns for OO, inheritance, etc, Javascript can compare admirably against Ruby. Not in every regard, but then there are actually some aspects of JS that are superior (e.g. functions as opposed to blockism; dynamic member creation).
* There's a lot more known about Javascript now, and it's almost certainly the most widely understood language in the industry, even though it's not the primary language for many (cf. English).
* Because of all the JS code now running in the browser, there are probably a bunch of synergies with server-side JS - these could be exploited by a well-considered server-side JS framework.

As an open platform, Phobos has the best chance right now to make server-side flourish. But I agree with Dion, that there is reason for concern about whether it will happen.
<blockquote>
Sun may already have this. Will they be able to market it? Unfortunately, the track record isnâ€™t there, so it will probably languish. Buy maybe not.
</blockquote>