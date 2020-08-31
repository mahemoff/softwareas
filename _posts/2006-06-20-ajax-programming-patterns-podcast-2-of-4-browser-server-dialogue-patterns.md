---
id: 312
title: 'Ajax Programming Patterns &#8211; Podcast 2 of 4: Browser-Server Dialogue Patterns'
date: 2006-06-20T15:52:07+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-programming-patterns-podcast-2-of-4-browser-server-dialogue-patterns
permalink: /ajax-programming-patterns-podcast-2-of-4-browser-server-dialogue-patterns/
dsq_thread_id:
  - "375572991"
categories:
  - Links
  - Podcast
  - SoftwareDev
tags:
  - AjaxPatterns
  - Cross-Domain
  - DHTML
  - Javascript
  - Links
  - Podcast
  - Polling
  - Proxy
  - Software
  - Throttling
  - Tutorial
  - Web
  - Web2.0
  - XML
---
Continuing from the previous podcast (*cough* 12 weeks ago), more programming patterns. <b>Unfortunately, this recording (and the next one) went pear-shaped. Sorry.</b> I do, however, recommend them to those of you who've been wondering what an Ajax talk would have sounded like in crackly 1930s recording technology, and one in which the speaker has a severe cold. FYI The level was too low and it didn't correct very well...maybe one day, I'll re-record, but for now I'd prefer to just get them out there as they have been sitting in the libsyn archive for many weeks.

The 40-minute podcast covers the following patterns:

<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Call_Tracking"
title="Call Tracking">Call Tracking</a> Accommodate busy user behaviour by
allocating a new XMLHttpRequest object for each request. See <a
href="http://smokey.rhs.com/web/blog/poweroftheschwartz.nsf/d6plinks/RSCZ-6CEQAR"
class='external text'
title="http://smokey.rhs.com/web/blog/poweroftheschwartz.nsf/d6plinks/RSCZ-6CEQAR"
rel="nofollow">Richard Schwartz's blog entry</a>.<b>Note:</b> Pending some
rewrite to take into account request-locking etc.</span>

</li><li> <span class="full"><a href="http://ajaxpatterns.org/Periodic_Refresh" title="Periodic Refresh">Periodic Refresh</a> The browser refreshs volatile information by periodically polling the server.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Submission_Throttling" title="Submission Throttling">Submission Throttling</a> Instead of submitting upon each Javascript event, retain the data in a local buffer and upload it periodically.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Explicit_Submission" title="Explicit Submission">Explicit Submission</a> Instead of submitting upon each Javascript event, require the user to explicitly request it, e.g. submit upon clicking a button.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Distributed_Events" title="Distributed Events">Distributed Events</a> Keep objects synchronised with an event mechanism.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Cross-Domain_Proxy" title="Cross-Domain Proxy">Cross-Domain Proxy</a> Allow the browser to communicate with other domains by server-based mediation.</span>
</li></ul>

<a href="http://softwareas.com/media/mahemoff/SASDAjaxProgrammingPatterns2of4.mp3"
title="Click to download the Podcast and play it on your computer."
style="text-decoration: none;"><img src="/images/aquapodcastfileicon.gif"
border="0" alt="Click to download the Podcast. You can also subscribe to the
feed if you want future podcasts automatically downloaded - check out the
podcast FAQ at http://podca.st." border="0"/></a>

This podcast covers six patterns on Browser-Server Dialogue: Call Tracking, Periodic Refresh, Submission Throttling, Explicit Submission, Distributed Events, 

Thanks for your feedback since last time. Good, bad, or ugly, it's all welcome - in the comments for this podcast or michael@mahemoff.com.<!--c808cf565357e90a6bc603b31c02a21c-->