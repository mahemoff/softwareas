---
id: 596
title: Will Bespin really end up with multiple backends?
date: 2009-08-18T22:04:12+00:00
author: admin
layout: post
guid: http://softwareas.com/will-bespin-really-end-up-with-multiple-backends
permalink: /will-bespin-really-end-up-with-multiple-backends/
dsq_thread_id:
  - "375574380"
categories:
  - SoftwareDev
tags:
  - Bespin
  - IDE
  - open source
  - Shindig
  - Software
---
<a href="http://groups.google.com/group/bespin/browse_thread/thread/44ead8a1d438496">Google groups thread</a>

Bespin has the idea of multiple backends attaching to the same client.
Right now, Python is apparently "winning" while Java has fallen behind
and PHP appears to have faded away.

The situation is very analogous to Shindig
(http://incubator.apache.org/shindig/) which has a strong Java
back-end, a PHP back-end that took a long time to get started in
earnest and AFAICT from a quick glance has tapered off, and a number
of non-starters.

I do wonder whether something like this is really viable - can you
have a vibrant ecosystem of back-ends in different languages? Granted,
there are hundreds of implementations of SMTP, FTP, and so on, in all
the languages of the rainbow. Those are actual protocols based on
strong standards. Likewise, Shindig had a fair crack at it because
it's based on the OpenSocial standard (but the diversity effort is
probably hampered by the fact that most companies who want to be
OpenSocial hosts tend to fall in the Java camp).

Bespin would need to formalise things and establish proper standards
to support multiple backends. Nothing as onerous as the IETF
standards, but still, they'd need to nail down all the subtle issues
and edge cases in order to support multiple backends. Good for
cleanliness perhaps, but at the expense of project velocity. Years
ago, I asked SpringSource's Rod Johnston about why one should use
Spring over the upcoming EJB3, and one of <a
href="http://www.theserverside.com/news/thread.tss?thread_id=27166#129081">his
reasons</a> - quite rightly - was that his code was available NOW
while the committee-driven EJB standard and subsequent implementations
were a long way off. In other words, Spring demonstrates that working,
open, code is in many respects far more powerful than a standard. I
can't imagine Bespin will want to formally document its protocols;
instead it will rely on code. But of course, if the code is a moving
target, how easy will it be for different backends to keep up?

Also, how motivated will the second, third, and fourth guys be? It's
more fun being the first to see the concept become reality; less so to
be building a port from one language to another. As with the previous
point, though, I stand to be corrected; some people might enjoy the
engineering challenge of building a parallel backend. (Maybe I'm being
solipsistic here, as I'm personally 20x more motivated by user stories
than implementation details.)

Java hosting is notoriously painful compared to the ease of cheap PHP
hosting, so I can see the argument for both; companies will want to
host Bespin on their own shiny enterprise Java servers, while
rebellious little startups will want to do the same thing for a sliver
of the cost on commodity iron.

<strong>Update:</strong> <a href="https://wiki.mozilla.org/Labs/Bespin/ServerAPI">Ben Galbraith responds</a>