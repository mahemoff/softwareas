---
id: 1462
title: 'Marcin Wichary: You Gotta Do What You gotta Do [Full Frontal Live Blog]'
date: 2011-11-11T17:42:53+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1462
permalink: /marcin-wichary-you-gotta-do-what-you-gotta-do-full-frontal-live-blog/
dsq_thread_id:
  - "468683155"
categories:
  - SoftwareDev
tags:
  - Conference
  - Javascript
---
Marcin explains the hacks that went into the Atari 2600, moving from a crappy
"tennis" game in 1978 to a somewhat less-crappy Pitfall in 1982, doing things the
Atari architects never anticipated. (Covered in "Racing the Beam") Which would
be the same if you showed 1990 TBL the web today.

Google Doodles have gotten bigger over the years ... lines of code:
2009: 1, 2010: 5000, 2011: 13000 
(thx @suhajdab)

Marcin shows various iterations of the underwater doodle:

<object width="560" height="315"><param name="movie" value="http://www.youtube.com/v/ve8pQp6fF00?version=3&amp;hl=en_US"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/ve8pQp6fF00?version=3&amp;hl=en_US" type="application/x-shockwave-flash" width="560" height="315" allowscriptaccess="always" allowfullscreen="true"></embed></object>

On the theme of pragmatism, it went through a bunch of iterations, to get to
the point where people would know they can control the water flow, ultimately
leading to an explicit handle control. And degrades gracefully to IE6 (choppy,
but works) and no-JavaScript (nice image).

We haven't gone beyond the IE6 graceful degradation...we still have this in
HTML5, so it's not going to go away. WebSocket keeps changing, different audio
support, etc. Which means you sometimes have to do what it takes.

Rality of JavaScript is if you don't do anything that feels a bit nasty, you're
a bit behind. So you have to embrace some of these nasty hacks. With doodles, the
endpoint is about doing something with a sense of purpose, not being infatuated
with the technology, or, for that matter, the art.


