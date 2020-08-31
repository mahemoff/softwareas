---
id: 248
title: Wikipedia as a Honeypot
date: 2005-12-07T01:48:13+00:00
author: admin
layout: post
guid: http://www.softwareas.com/wikipedia-as-a-honeypot
permalink: /wikipedia-as-a-honeypot/
dsq_thread_id:
  - "378639810"
categories:
  - HumansAndTech
tags:
  - Security
  - Usability
  - Visualization
  - Wiki
  - Wikipedia
---
How long until wikipedia becomes a honeypot?

<i>"Who wants to be a millionaire" contestant is struggling to answer the question, "What year did the Fonz jump the shark?", and calls out to Lifeline Buddy. Back in 2005, Lifeline Buddy would have googled for the answer. But this is 2007, and "wiki" is now a household name (the media refers to "wiki" and "wikipedia" interchangeably). Lifeline Buddy bangs out "fonz jump shark" into wikipedia's search field and quickly finds <a href="http://en.wikipedia.org/wiki/Jumping_the_shark">the right page</a>, reporting confidently the year was 1975. Only, it's wrong; Fonzarelli, of course, jumped the shark in 1977. The producers had entered the fraudulent details at precisely the moment the lifeline was consulted. Contestant takes his $1000 consellation and exits, muttering something about the Britannica under his breath.</i>

Producers wouldn't stoop so low? If the  BBC <a href="http://www.boingboing.net/2005/08/13/bbc_punks_wikipedia_.html">can do it</a>, draw your own conclusion. The Register, in any event, would have a field day with their <a href="http://www.theregister.co.uk/2005/12/06/wikipedia_bio/">latest whipping boy</a>.

Instead of restorting to restricting edits, **wikipedia first needs to try out a "heat map" view to help people decide how stable the information is.** Not as gaudy as the <a href="http://ajaxpatterns.org/">Ajax Patterns</a> authoring heatmap (using a more subtle theme now), but some way for people to know what's new and what's old. **Again, this comes back to the idea of <a href="http://www.softwareas.com/an-ajax-framework-a-day">separating out wiki content from presentation</a>, ideally using some kind of web service. A wiki needs more than one view, even without any Maps/Flickr/Delicious mashup.** For example, you could have three standard views:

* Pure wiki reading, just like wikipedia today.
* Stability view. e.g. Most content in white as now, but with a few shades of grey to distinguish how old each phrase is (darker grey = past minute, medium grey = past hour, light grey = past day; so a phrase "graduates" from grey to white as it matures).
* Inspection mode. Full-on data mining interface, using Ajax (of course) to explore history, drill down to author info, etc.
