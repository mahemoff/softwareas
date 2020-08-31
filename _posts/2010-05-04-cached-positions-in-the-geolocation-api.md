---
id: 880
title: Cached Positions in the Geolocation API
date: 2010-05-04T23:37:06+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=880
permalink: /cached-positions-in-the-geolocation-api/
dsq_thread_id:
  - "375773926"
categories:
  - SoftwareDev
tags:
  - Geolocation
  - html5
---
<img src="http://picupper.com/2010/05/04/here.jpg" />

The <a href="http://dev.w3.org/geo/api/spec-source.html">Geolocation API</a> is surprisingly short and simple. A simple lookup is a doddle:

[javascript]
navigator.geolocation.getCurrentPosition(function(position) {
  alert("You're at " + position.coords.latitude + ","
          + position.coords.longitude);
});
[/javascript]

About the most complicated thing is "cached positions", and even those are quite straightforward. So what's that all about?

A cached position is what the API returns when you don't need a live, "this is where the user is right now", position. Geo-lookups can be time-consuming, so sometimes you might opt for a slightly stale location instead of making the user wait for a lookup. You might also be helping the user to reduce battery life or bandwidth consumption.

In the simplest usage, a real lookup will always occur:
[javascript]
navigator.geolocation.getCurrentPosition(showMap); // no options? no cache for you.
[/javascript]

However, you can also say "I'll happily accept a location from the past minute (60,000 ms) if you know it"
[javascript]
navigator.geolocation.getCurrentPosition
  (showMap, handleError, {maximumAge:60000});
[/javascript]

Set maximumAge as Infinity (a valid Javascript literal) to say "just give me a cached value you cached <em>any</em> time, I don't care how far back".

Using a second <tt>timeout</tt> parameter, you can <strong>force</strong> the position to be cached, i.e. prevent a lookup altogether, even if there's no cached value, in which case you get an error.

[javascript]
navigator.geolocation.getCurrentPosition
  (showMap, handleError, {maximumAge:60000, timeout:0});
[/javascript]

(The spec uses "position" and "location" interchangeably; ideally a spec like this would use a single term, but at least in this case they do mean almost the same thing.)