---
id: 202
title: 18 New Ajax Programming Patterns
date: 2005-09-16T19:09:05+00:00
author: admin
layout: post
guid: http://www.softwareas.com/18-new-ajax-programming-patterns
permalink: /18-new-ajax-programming-patterns/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572585"
  - "375572585"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Javascript
  - JSON
  - Links
  - Patterns
  - REST
  - RPC
  - SOAP
  - Web2.0
  - XML
---
**I've uploaded full text for [18 new Ajax patterns](http://ajaxpatterns.org), completing a first-cut draft for all Programming Patterns content, which will be one part of the book. This section bridges the gap between the very basics of Ajax - XMLHttpRequest, DOM, etc - and the high-level stuff like widgets and visual effects.** For instance, how do you do design the services accessed by XMLHttpRequest? Or how do you deal with a lots of Javascript? The focus here is on traditional tech concerns such as maintainability and understandability; and less about usability.

Breaking it down:

* **Web Services** patterns are about overall browser-server architecture - what kinds of services and what kinds of messages? It's relevant to the conversation of [Jon Tiersen](http://blogs.codehaus.org/people/tirsen/archives/001154_designs_for_remote_calls_in_ajax.html) and others about what sort of responses are possible - XML, JS, HTML, JSON. It's also relevant to another recent conversation, on [http://www.theserverside.com/news/thread.tss?thread_id=35979 Ajax and webservices], as it covers REST and RPC.

* **Browser-Server Dialogue** covers a mixed bag of patterns about XMLHttpRequest handling and what you can do with it, such as loading JS on demand.

* **DOM Population** is about transforming incoming XML into DOM content, e.g. XSLT.

* **Performance Optimisation** covers a variety of performance patterns such as caching and pre-fetching.

* **Breakout** (can you think of a better name) is about going beyond standard Ajax constraints, namely using a server-side mediator to access external domains and introducing a plugin to go where no Ajax app is allowed to go.

* **Code Generation and Reuse** is strongly  related to some of <a href="http://ajaxpatterns.org/Ajax_Frameworks">the emerging frameworks</a> like Echo2 and SAJAX.

This is all **early** days, so any feedback on the structure, names, or content will be taken into account and acknowledged too (really!). OK, here's the lot ...

<div class="editsection" style="float:right;margin-left:5px;"></div><a name="Programming_Patterns_.2840.29"></a><h1> Programming Patterns</h1>
<div class="editsection" style="float:right;margin-left:5px;"></div><a name="Web_Services"></a><h2> Web Services </h2>

<ul><li> <span class="full"><a href="http://ajaxpatterns.org/RESTful_Service" title="RESTful Service">RESTful Service</a> Expose web services according to RESTful principles.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/RPC_Service" title="RPC Service">RPC Service</a> Expose web services as Remote Procedural Calls (RPCs).</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/HTML_Response" title="HTML Response">HTML Response</a> Have the server generate HTML snippets to be displayed in the browser.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Semantic_Response" title="Semantic Response">Semantic Response</a> Have the server respond with abstract, semantic, data.</span>

</li><li> <span class="full"><a href="http://ajaxpatterns.org/Plain-Text_Message" title="Plain-Text Message">Plain-Text Message</a> Pass simple messages between server and browser in plain-text format.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/XML_Message" title="XML Message">XML Message</a> Pass messages between server and browser in XML format.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/JSON_Message" title="JSON Message">JSON Message</a>  Pass messages between server and browser in Javascript Object Notation (JSON) format.</span>
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;"></div><a name="Browser-Server_Dialogue"></a><h2> Browser-Server Dialogue  </h2>

<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Call_Tracking" title="Call Tracking">Call Tracking</a> Accommodate busy user behaviour by allocating a new XMLHtpRequest object for each request. See <a href="http://smokey.rhs.com/web/blog/poweroftheschwartz.nsf/d6plinks/RSCZ-6CEQAR" class='external' title="http://smokey.rhs.com/web/blog/poweroftheschwartz.nsf/d6plinks/RSCZ-6CEQAR" rel="nofollow">Richard Schwartz's blog entry</a></span><span class='urlexpansion'>&nbsp;(<i>http://smokey.rhs.com/web/blog/poweroftheschwartz.nsf/d6plinks/RSCZ-6CEQAR</i>)</span>.<b>Note:</b> Pending some rewrite to take into account request-locking etc.
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Distributed_Events" title="Distributed Events">Distributed Events</a> Keep objects synchronised with an event mechanism.</span>

</li><li> <span class="full"><a href="http://ajaxpatterns.org/On-Demand_Javascript" title="On-Demand Javascript">On-Demand Javascript</a> Download Javascript as and when required, instead of downloading it all on page load.</span>
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;"></div><a name="DOM_Population"></a><h2> DOM Population </h2>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/XML_Data_Island" title="XML Data Island">XML Data Island</a> Retain XML responses as "XML Data Islands", nodes within the HTML DOM.</span>

</li><li> <span class="full"><a href="http://ajaxpatterns.org/Browser-Side_XSLT" title="Browser-Side XSLT">Browser-Side XSLT</a> Apply XSLT to convert </span><span class="full"><a href="http://ajaxpatterns.org/XML_Message" title="XML Message">XML Messages</a> into XHTML.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Browser-Side_Templating" title="Browser-Side Templating">Browser-Side Templating</a> Produce browser-side templates and call on a suitable browser-side framework to render them as HTML.</span>
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;"></div><a name="Performance_Optimisation"></a><h2> Performance Optimisation </h2>

<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Fat_Client" title="Fat Client">Fat Client</a> Create a rich, browser-based, client by performing remote calls only when there is no way to achieve the same effect in the browser.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Browser-Side_Cache" title="Browser-Side Cache">Browser-Side Cache</a> Maintain a local cache of information.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Guesstimate" title="Guesstimate">Guesstimate</a> Instead of grabbing real data from the server, make a guesstimate that's good enough for most user's needs.
</span></li><li> <span class="full"><a href="http://ajaxpatterns.org/Submission_Throttling" title="Submission Throttling">Submission Throttling</a> Instead of submitting upon each Javascript event, retain the data in a local buffer and upload it periodically.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Explicit_Submission" title="Explicit Submission">Explicit Submission</a> Instead of submitting upon each Javascript event, require the user to explicitly request it, e.g. submit upon clicking a button.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Multi-Stage_Download" title="Multi-Stage Download">Multi-Stage Download</a> Quickly download the page structure with a standard request, then populate it with further requests.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Predictive_Fetch" title="Predictive Fetch">Predictive Fetch</a> Anticipate likely user actions and pre-load the required data.</span>

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;"></div><a name="Breakout"></a><h2> Breakout </h2>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Cross-Domain_Mediator" title="Cross-Domain Mediator">Cross-Domain Mediator</a> Allow the browser to communicate with other domains by server-based mediation.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Richer_Plugin" title="Richer Plugin">Richer Plugin</a> Make your application "more Ajax than Ajax" with a Richer Plugin.</span>

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;"></div><a name="Code_Generation_and_Reuse"></a><h2> Code Generation and Reuse </h2>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Ajax_Stub" title="Ajax Stub">Ajax Stub</a> Use an "Ajax Stub" framework which allows browser scripts to directly invoke server-side operations, without having to worry about the details of XMLHttpRequest and HTTP transfer.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Server-Side_Code_Generation" title="Server-Side Code Generation">Server-Side Code Generation</a> Automatically generate HTML and Javascript from server-side code.</span>

</li><li> <span class="full"><a href="http://ajaxpatterns.org/Cross-Browser_Component" title="Cross-Browser Component">Cross-Browser Component</a> Create cross-browser components, allowing programmers to reuse them without regard for browser compatibility.</span>
</li></ul>

<hr />

**Aside** I was interviewed yesterday for a Japanese magazine about how I'm using the wiki. So maybe some people will be interested to know that I always write the patterns offline because I am more creative in Vim and also to avoid textarea hell. (So much for Writely, will anyone create Vimly, there's gotta be more money it than cloning MS-Word online :-D). I also use the Mozex or ViewSourceWith extensions to make partial edits using Vim.

This time, I decided not to upload once or twice at a time; but instead all 18 at once.
There's serious overhead of introducing each new pattern to the wiki (from Vim, the sequence is: 2mins spell-check, 5-10mins markup massaging, 2 mins fixing the link and description on the homepage; sometimes exacerbated by server lag.) Uploading all at once at least allowed me to focus fully on the task and also made some aspects more efficient, particularly updating the homepage.)