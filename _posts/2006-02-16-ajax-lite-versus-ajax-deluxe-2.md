---
id: 268
title: Ajax Lite Versus Ajax Deluxe
date: 2006-02-16T16:30:55+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-lite-versus-ajax-deluxe
permalink: /ajax-lite-versus-ajax-deluxe-2/
dsq_thread_id:
  - "375572791"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Architecture
  - HTML
  - Javascript
  - Links
  - Polymorphic Podcast
  - Software
  - Web2.0
---
<img align="right" src="http://img113.imageshack.us/img113/42/fuddruckersbigburger6zh.jpg"  width="200" style="padding: 8px;"/>
Harry Fuecks suggests [there are two types of Ajax apps](http://www.sitepoint.com/blogs/2006/02/15/two-kinds-of-ajax-html-vs-client-soa/): HTML++ and Client/SOA. This is something I've noticed too, and it cuts right across the Ajax architecture, impacting on the user-interface, the physical architecture (browser-server separation) and the abilities of the developers involved.

The "Ajax App" pattern addresses this as a decision. It's the root pattern for the entire Ajax Patterns language (Ajax App is not yet on <a href="http://ajaxpatterns.org">the AjaxPatterns wiki</a>). As you might know, each pattern has a "Decisions" section, identifying the decisions you'll have to make if you go with the pattern. In the case of Ajax App, a big decision is how far along the spectrum you go. I've termed them differently to Harry, but the distinction is essentially the same (there's now a footnote to his article). Extract from the "Ajax Design Patterns" draft:

<h4 class="title"><a name="id731758"></a>Will your application be "Ajax Deluxe" or "Ajax Lite"?</h4><p>There are two archetypal architectures for Ajax, and all
              applications lie somewhere along the spectrum between these extremities:
              </p><div class="variablelist"><dl><dt><span class="term">Ajax Deluxe</span></dt>

<dd><p>
                <strong>Ajax Deluxe uses Ajax to the max: applications feel similar to a
                desktop in that the browser is driving the interaction - it
                mediates all interaction between the user and server, so there
                are no - or few - direct page refreshes.</strong> Similarly, there's no
                - or little - session tracking in the server, because all
                relevant state can be managed inside the browser. The server
                may not know about HTML at all, and just offer generic web
                services. An example is the Ajax word processor, <a href="http://writely.com" target="_top">Writely</a>.
              </p></dd><dt><span class="term">Ajax Lite</span></dt><dd><p>
                <strong>An Ajax Lite App feels more like a conventional web app overall,
                but one that's been sprinkled with Ajax here and there.</strong> For
                instance, Ajax might be used to validate a form before it's
                submitted using standard form submission, or to reveal some
                instructions on the page when a user requests help. An example
                is <a href="http://del.icio.us" target="_top">Delicious</a>, which
                works fine on legacy browsers, but offers Ajax <a href="http://ajaxpatterns.org/Suggestion">Suggestions</a> for the many
                browsers that support it.
              </p></dd></dl></div>

<p>
            Which will you use? The Deluxe approach suits a development team
            with more advanced web programming knowledge and access to relevant tools and cross-browser libraries, and it will generally
            lead to a nicer, more effective, user-interface. It also
            facilitates a well-partitioned architecture, since the presentation
            logic can be isolated inside the browser and the business logic
            isolated in the server.  However, Deluxe applications may place a
            strain on the browser and network capabilities, and might not even
            be possible if the browser is outdated. Ajax Lite is a better
            answer for older browsers, since the Ajax features can usually be
            "turned off" to support graceful degradation.
          </p>


<img align="left" src="http://img109.imageshack.us/img109/6894/ssandwhich2as.jpg" width="200" style="padding: 8px;"/>

<strong>Epilogue:</strong>Another nice way to say this: "Ajax Deluxe" (or Client/SOA) == <b>"Ajax Application"</b>, "Ajax Lite" (or HTML++) == <b>"Ajax Website"</b>. The "Application" versus "Website" terminology was mentioned by Craig in the latest Polymorphic Podcast, <a href="http://polymorphicpodcast.com/shows/architectajax/">Architecting Ajax Applications</a>. If you want to hear more about the Ajax patterns (and since I'm so slow to complete my own podcasts on the topic, but I promise it will happen eventually!), check out this podcast, which is mostly about Craig's take on <a href="http://ajaxpatterns.org">Ajax Patterns</a>. He's not just regurgitating the patterns either, as he offers many fresh ideas and examples.