---
id: 279
title: 'Comet: It&#8217;s Ajax for &#8220;Push&#8221; (Podcast)'
date: 2006-03-05T08:04:29+00:00
author: admin
layout: post
guid: http://www.softwareas.com/comet-its-ajax-for-push
permalink: /comet-podcast/
enclosure:
  - |
    http://softwareas.com/podcast/SASDCometItsAjaxForPush.mp3
    27166653
    audio/mpeg
  - |
    http://www.softwareas.com/podcast/SASDCometItsAjaxForPush.mp3
    27166653
    audio/mpeg
dsq_thread_id:
  - "375572807"
categories:
  - HumansAndTech
  - Links
  - Podcast
  - SoftwareDev
tags:
  - AjaxPatterns
  - Comet
  - DHTML
  - HTTP
  - Javascript
  - Links
  - Podcast
  - Push
  - Pushlet
  - Streaming
---
<img src="http://img134.imageshack.us/img134/2433/comet7aq.gif" />

Here's a podcast about Comet - exploring the two-way web with Ajax.
From <a href="http://ajaxian.com/archives/comet-a-new-approach-to-ajax-applications">my Ajaxian post</a> earlier today:

<blockquote>
<a href="http://alex.dojotoolkit.org/?p=545">Alex Russell has coined a term</a> for a flavour of Ajax that&#8217;s been getting more attention of late. <b>Comet</b> describes applications where the server keeps pushing - or <a href="http://ajaxpatterns.org/HTTP_Streaming">streaming</a> - data to the client, instead of having the browser <a href="http://ajaxpatterns.org/Periodic_Refresh">keep polling</a> the server for fresh content. Alex identifies several buzzworthy examples:
</blockquote><blockquote>
	<ul>
	<li><a href="http://mail.google.com/mail/help/chat.html">GMail&#8217;s GTalk integration</a></li>
	<li><a href="http://jotlive.com">Jot Live</a></li>
	<li><a href="http://renkoo.com">Renkoo</a></li>
	<li><a href="http://cgiirc.sourceforge.net/">cgi:irc</a></li>
	<li><a href="http://meebo.com">Meebo</a></li>
	</ul>
</blockquote>

This is an important article because it captures a growing trend in Ajax, a trend I had in mind when I said we expect to hear more about "Push and the Two-Way Web" in the next twelve months, on the occasion of <a href="http://ajaxian.com/archives/happy-birthday-ajax">Ajax's birthday</a>. There will, of course, be people saying "there's nothing new here", and that's presumably all too obvious to Alex himself, who has worked with these ideas for a long time. But as with Ajax, it's the power of a name. I don't think these ideas can adequately be described as Ajax, because Ajax changes a lot about the browser whereas Comet fundamentally changes the nature of browser-server communication. I see Comet as part of the overall Ajax trend, complementary to the UI aspects of Ajax.

People may also say there are existing names like "Push". True, but they have baggage - I think it's useful to have a name for this architectural pattern in light of the relationship to Ajax.

Anyways, I wanted to expand on some of the thoughts in the article and after the recent Basics of Ajax Podcast, I'm in the mood for more audio rambling. So here's a 56-minute discussion about Comet and the general trend of push and streaming within Ajax.

<a href="http://www.softwareas.com/podcast/SASDCometItsAjaxForPush.mp3"
title="Click to download the Podcast and play it on your computer."
style="text-decoration: none;"><img src="/images/aquapodcastfileicon.gif"
border="0" alt="Click to download the Podcast. You can also subscribe to the
feed if you want future podcasts automatically downloaded - check out the
podcast FAQ at http://podca.st." border="0"/></a>

Shownotes...

<pre>

It's the Duplex, Stupid!
  Push or Pull - it doesn't matter so much. What's critical here
  is the focus on the two-way web.

Applications
  - Chat
  - Wiki
  - News - Current events, sport, financials, etc
  - Trading and Auctions
  - Real-time control and logistics
  - File transfer (combine with local storage)
  - Any other genre you'd care to name

Vanilla Ajax: Await the User

Comet Ajax: Keep Pushing

Polling Ajax: Keep Pulling

Benefits of Comet
  - Responsive: data pumped out immediately
  - More stable profile
  - Less overhead of establishing connections

Benefits of Polling
  - Browser memory
  - Can run on any standard server; Comet requires suitable
    server
  - Can upload at the same time
  - Can run on  - with Comet, XHR and IFrame won't always reflect
    changes while the connection's open
  - Being more standard, works with existing infrastructure.
    Comet is vulnerable to middle-men dropping the connection.
  - Simpler architecture - only the browser's in control
  - Easier to test
  - More familiar architecture
  - Less programming effort - with Comet, must watch for changes
    on the stream
  - More efficient for infrequently accessed data
  - Leverages caching

Maybe Comet causes more pain, but if it keeps the user happy ...

Questions and Trends
  - Which to use. Variables include: frequency of updates,
    importance of updates, server capabilities, target browsers
  - Dealing with incoming messages, e.g.  Distributed Events
    pattern, Event bus (browser or server?), etc
  - Workarounds for throbber, status bar, clicking sound, etc.
  - How often to drop connections
  - How browsers can accommodate it

Proof-Of-Concept Demos
- <a href="http://ajaxify.com/run/wiki">Wiki using Periodic Refresh/Polling</a>
- <a href="http://ajaxify.com/run/wiki/streaming">Wiki using <span style="text-decoration: line-through;">HTTP Strea</span>uh, Comet</a>
   (Actually, this is only a very basi implementation -
    there's no use of events, just custom handling of HTTP.

Related Patterns
- <a href="http://ajaxpatterns.org/HTTP_Streaming">HTTP Streaming</a>
- <a href="http://ajaxpatterns.org/Periodic_Refresh">Periodic Refresh (aka Polling)</a>
- <a href="http://ajaxpatterns.org/Distributed_Events">Distributed Events</a>
</pre>

As always, feedback is welcome - michael@mahemoff.com<!--3211e483ebcc46ba6cfa52b027a8b6e5-->