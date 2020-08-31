---
id: 325
title: 'Two-Way Web: Can You Stream In Both Directions?'
date: 2006-07-13T22:42:09+00:00
author: admin
layout: post
guid: http://www.softwareas.com/two-way-web-can-you-stream-in-both-directions
permalink: /two-way-web-can-you-stream-in-both-directions/
dsq_thread_id:
  - "375573016"
categories:
  - SoftwareDev
tags:
  - CollaborativeWeb
  - Comet
  - Duplex
  - HTTP
  - Push
  - Streaming
  - Two-Way Web
---
<img src="http://img528.imageshack.us/img528/1461/duplexcomet7mj.png">

<i><b>Update (couple of hrs later):</b> I mailed Alex Russell (the guy who named Comet and knows plenty about it), it sounds like he's been investigating this whole area and he's sent me his views.</b></i>

We know about <a href="http://softwareas.com/Comet">Comet</a> (AKA Push, <a href="http://ajaxpatterns.org/HTTP_Streaming">HTTP Streaming</a>) and its ability to keep streaming info from server to browser. <b>How about streaming upwards, from browser to server, and preferably in the same connection?</b> A reader mailed me this query:

<blockquote>
<p>Im missing one demo, would it be possible to reuse same stream in
streaming demos to send msg to server, I've been digging throw your
examples, but they all seem to
create a new connection to the server when posting, would be very
interesting see a demo that does this within the same stream, and of
course the server code would be as interesting as the client.
</blockquote>

Here's my thinking, I'm sure a lot of smart readers will know more about this and I'll be interested in your views - is it feasible? Any online demos?
<blockquote>
<p>Unfortunately, I've not seen anyone pull this off - it's always assumed you need a "back channel". It's the kind of hack someone like Google or 37S would turn around and pull off even though it's "obviously impossible"  ;-) .

<p>There are two key issues:
<p>(1) Server needs to start outputting before incoming request is finished. With a specialised server, this problem could be overcome.
<p>(2) (More serious as we can't control the browser) The browser would need to upload data in a continuous stream. You can do it with Flash/Java, but I can't see how to do this with standard JS/HTML. If you use XHR, you're going to call send() and wave goodbye to the entire request...there's no support for sequencing it. Same if you submit a regular form, change IFrame's source etc. Even if you could somehow delay reading of content so it's not immediately uploaded, the browser would probably end up not sending anything at all as it would be waiting to fill up a packet.

<p>I think the solution lies in the <a href="http://httpd.apache.org/docs/1.3/keepalive.html">Keep-Alive</a> extension to HTTP 1.1:
<blockquote>
<p>What is Keep-Alive?
<p>The Keep-Alive extension to HTTP, as defined by the HTTP/1.1 draft, allows persistent connections. These long-lived HTTP sessions allow multiple requests to be send over the same TCP connection, and in some cases have been shown to result in an almost 50% speedup in latency times for HTML documents with lots of images.
</blockquote>

<p>If you google for "xmlhttprequest keep-alive" or "ajax keep-alive", you'll see people talking about the idea a bit, but there's not much info on how to script it for continuous connections and no demos to be found. It would make a great experiment if someone did a proof-of-concept!

<p>As an alternative, you could consider a thin, invisible, Flash layer to handle transport, and degrade to frequent <a href="http://ajaxpatterns.org/Submission_Throttling">Submission Throttling</a> where Flash isn't an option.
</blockquote>

<p>BTW I have a post and podcast planned about the whole two-way web thing, which will be profound (the two-way web thing, not the podcast :-)). The web is entering a new era of Real-Time Collaboration and Communication, post-Ajax (and of course building on Ajax, just as Ajax builds on the technologies of the previous era: CGI, DHTML, CSS, etc).

Update: As mentioned above, Alex Russell mailed me his views. In particular, it's interesting to consider the possibility that browsers might transparently exploit keep-alive if you hit the server frequently enough.
<blockquote>
<p>So I've spent some time investigating this (as you might expect), and at 
the end of the day there's not much to be done aside from using Flash 
and their XMLSocket interface. That's an obvious possibility given the 
high-performance Flash communication infrastructure we have in Dojo. 
Doing bi-directional HTTP probably won't happen, though, but I don't 
think that's cause for despair. In my tests, we can get really good 
(relative) performance out of distinct HTTP requests so long as the 
content of the request is kept to a minimum and the server can process 
the connection fast enough. HTTP keepalive exists at a level somewhat 
below what's currently exposed to browsers, so if the client and server 
support it, frequent requests through stock XHR objects may verywell be 
using it anyway. We'll have to do some significant testing to determine 
what conjunctions of servers/clients might do this, however.

<p>There are even more exotic approaches available from Flash peering that 
I've been investigating as well, but they will require significantly 
different infrastructure from what we already deploy that I think 
they're still in the land of "hrm...someday". 

<p>First we have to solve the *regular* Comet scalability problems for 
existing servers and app containers.

<p>Regards

<p>PS: we haven't been making much noise about it, but serious work has 
started on an Open Source Comet protocol with initial implmemntations 
in both Perl and Python over at http://cometd.org. The initial client 
library is Dojo-based, but we'll be publishing the protocol so that 
anyone can "play" with it.
</blockquote>