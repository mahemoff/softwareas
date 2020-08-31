---
id: 122
title: 'AJAX Patterns: Design Patterns for AJAX Usability'
date: 2005-05-08T03:24:17+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-patterns-design-patterns-for-ajax-usability
permalink: /ajax-patterns/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375268206"
  - "375268206"
categories:
  - Links
  - SoftwareDev
---
<span class="intro">I've been putting together some AJAX design patterns.</span>

**Update (May 15, 2005):** I've set up [AJAXPatterns.org](http://ajaxpatterns.org) to keep working on these patterns. I've also cleaned up a couple of things here, although all future changes will occur at ajaxpatterns. Thanks to Leoglas for spotting two errors here.

## Why AJAX Design Patterns?

[AJAX](http://www.adaptivepath.com/publications/essays/archives/000385.php) holds a lot of promise for web usability, and the underlying technology has already delivered some [stunning](http://maps.google.com/)  [applications](http://www.francisshanahan.com/zuggest.aspx). But it's no magic bullet. Careful design is always required, and it must be based specifically on the technology at hand. As AJAX emerges, we're going to learn more about what sort of design works, and we'll need ways of documenting this information and talking about it. Fortunately, the evolution of this particular technology will take place at a time when design patterns are well-entrenched in the industry, and design patterns are an excellent means of knowledge representation. Thus, it makes sense to begin cataloguing AJAX design patterns.  These are some thoughts based on current examples and demo systems.

Patterns being patterns, there's not a lot of unseen information here. Patterns are just a concise way to represent the knowledge embodied in the many AJAX applications that are out there. The point is to discover best practices by investigating how developers have successfully traded off conflicting design principles. AJAX is all about usability, so the patterns focus particularly on delivering usability in the face of constraints, most notably: user capabilities and expectations, bandwidth limits, the stateless nature of HTTP, the complexity of Javascript.

This is a work-in-progress. There should eventually be more patterns, more examples, more detailed explanations. And one more disclaimer: AJAX is a new term, but XMLHttpRequest and related technologies have been around for a while. I know that, but the introduction of a single umbrella term nevertheless constitutes a tipping point which is forcing web development to move heavily in a certain direction. AJAX is only a name, but names can be tremendously important.

## Related Work

* [Thomas Baekdal's AJAX Usability Guidelines](http://www.baekdal.com/articles/Usability/XMLHttpRequest-guidelines) contains some great advice and inspired me to write these patterns. What I'm doing here is not just stating different guidelines. [Patterns ain't principles](http://mahemoff.com/paper/principles/), and the focus here is on patterns whereas the focus above is on principles. Both forms of design advice are vital. Here, I'm explicitly distinguishing between the two, because the patterns are intended to help designers achieve the principles. The principles here are heavily influenced by Baekdal's guidelines.

* [fiftyfoureleven.com](http://www.fiftyfoureleven.com/resources/programming/xmlhttprequest/examples#L-240) and [AJAX Matters](http://www.ajaxmatters.com/)  contain great collections of AJAX examples. You can't have patterns without examples.

* [Joel Webber](http://jgwebber.blogspot.com/2005/02/mapping-google.html) illuminates the technology behind Google Maps. [Chris Justus](http://serversideguy.blogspot.com/2004/12/google-suggest-dissected.html) dissects Google Suggest.

* The recent [AJAX podcast and blog entry](http://www.softwareas.com/ajax-podcast) covered some of the strengths and weaknesses of AJAX. The patterns here are supposed to guide on emphasising the strengths of AJAX without being struck by its weaknesses. The Polymorphic Podcast has also [covered](http://www.drazz75.com/2005/03/25/) [AJAX](http://www.drazz75.com/2005/04/14/) - prior to my podcast and is recommended as alternative overview on the technology.

## Design Principles for AJAX Applications

* **Minimise traffic between browser and server** so that the user feels the application is responsive.
* **Be clear on the interaction mode being used - regular HTML versus AJAX versus desktop application** so that the user can predict what will happen next .. no surprises.
* **While avoiding confusion, borrow from conventions of HTML and desktop applications** so that the user can rapidly learn how to use your application.
* **Avoid distractions such as gratuitous animations** so that the user can focus on the task at hand.
* **Stick with AJAX wherever possible - just say no to entire page downloads** so that the user's experience is consistent.
* **Adopt AJAX for usability, not just to illustrate you're hip to where it's at** so that the user is engaged, and not immediately driven away by your nod to website splash screens, &lt;blink tags&gt;, popup ads, and other usability disasters of websites which have gone to a place you don't want to be.

Some (and eventually all?) of these principles above inform the patterns below. The patterns are about trading off among the principles, and also about resolving conflict between the needs of usability and other practical constraints, such as ease-of-development.

## Architectural Patterns

<span class="pattern">
**Local Event-Handling** You want the user experience to be dynamic and responsive, but it slows things down if you have to keep going to the server. THEREFORE, **ensure most events are handled locally, resorting to server-side interaction only when there is no local facility**. To increase the cases where local handling is sufficient, consider using **Local Caches**.
</span>

<span class="pattern">
**Local Cache** You want to support **Local Activity**, but many events must be handled by resorting to data on the server. THEREFORE, **maintain a local cache of information**. The cache might be created on initialisation or accumulated after each query. When accumulating upon query, it's probably worthwhile performing a **predictive download**. 

* Example: Websites have kept local information at hand for many years. Many forms cache a mapping from countries to states, for instance.
</span>

<span class="pattern">
**Predictive Download** You want the application to respond quickly, but many user actions will require information from the server. THEREFORE, **anticipate likely user actions and pre-load the required data**. Note that this auxiliary information should ideally be downloaded after the main information has been loaded. A "background thread" might even be used to continuously monitor the user's local behaviour, regularly pulling down information which might be useful.

* Example: [Google Maps](http://maps.google.com/) downloads more than you ask, evidenced by the fact that you can move a little in each direction without forcing any new blocks to be loaded. Another way to see this is to compare what happens when you pan slowly versus quickly. Another example is
[International Herald Tribune](http://www.iht.com/), which caches entire articles to provide immediate gratification when you click on "next page" (an example taken from [here](http://www.oreillynet.com/pub/wlg/6782). Google asks the browser to [prefetch the first search result](http://blog.searchenginewatch.com/blog/050331-180020) in case the user clicks on it.
</span>

<span class="pattern">
**Submission Throttling** You want the application to respond quickly, but it will be overloaded if the server was accessed for every trivial input event. THEREFORE, **instead of submitting upon each Javascript event, use the events to change local state**. Store events in a buffer variable, or some DOM component, and frequently (e.g. once a second) poll to see if anything should be submitted. As a variant to periodic polling, check the time since last submission whenever a new Javascript event occurs. Note: If the period is long (e.g. 10 minutes), show the **Synchronisation Status** and consider allowing explicit submission as well.

 * Example: Instead of submitting upon keypress, Google Suggest [uses setTimeout() to periodically check if the input field has changed](http://serversideguy.blogspot.com/2004/12/google-suggest-dissected.html).
</span>

<span class="pattern">
**Explicit Submission** (An alternative to Submit Throttling.) You want the application to respond quickly, but it will be overloaded if the server was accessed for every trivial input event. THEREFORE, **instead of submitting upon each Javascript event, require the user to explicitly request it, e.g. submit upom clicking a button**. Ensure the user knows what's been submitted with **Synchronisation Status**.

* Example: Like many chat applications, [the LiveChat demo](http://www.plasticshore.com/projects/chat/index.html)  requires you to click a "submit" button in order to complete your chat message.
</span>

<span class ="pattern">
**Periodic Refresh** You want the browser to be synchronised with the server, but information may change server-side after the user last made a change (e.g. because of another user on the same system). THEREFORE, **the browser should periodically call the server so as to refresh any volatile information**. Furthermore, indicate information staleness is with **Age Displays**.

* Example:  Open two browsers, and you'll see that [this chat demo](http://www.plasticshore.com/projects/chat/index.html) polls the server for changes every few seconds.
</span>

<span class="pattern">
**Distinct URLs** You want to let users send and bookmark information, but the application is dynamic and the results of XMLHttpRequest interaction will not alter the URL. THEREFORE, **use a URL-based scheme or write distinct URLs whenever the input will cause a fresh new browser state, one that does not depend on previous interaction**.

* Example: [A9](http://a9.com) interacts via AJAX, but nevertheless provides a clean URL when you perform a new search. [Google Maps](http://maps.google.com) has a "Link to this Page" link, which will always provide a link to whatever the user is looking at.</span><span>

## Display Patterns

</span><span class="pattern">
<b>Rich CSS</b> You want the user-interface to be rich and colourful, but you have to minimise download size in order to make the interface responsive. THEREFORE, **lean heavily on CSS to give a rich, graphical, appearance, without having to download images**.
</span>

<span class="pattern">
**Embedded Text** You want the-user interface to be rich and graphical, but you need plain text in order to support standard web functionality such as cut-and-paste and inspection by search engine robots. THEREFORE,**integrate text into graphics, and rely on *Rich CSS* to show text when fancy styling is desirable**.

* Example: The address balloon in [Google Maps](http://maps.google.com/).
</span>

<span class="pattern">
**Age Display** You want the user to trust the system, but it's possible some information on the browser is stale. THEREFORE, **indicate the age of any critical information**. Vary background brightness, for instance.

* Example: [SkyScanner](http://skyscanner.net) is a non-AJAX price comparison site which shows how old its prices are. Many trading applications do likewise with stock quotes. I'm not aware of any AJAX examples at this stage; this pattern is purely speculative and likely to be relevant only to public websites which cannot justify frequent updates.
</span>

<span class="pattern">
**Synchronisation Status** You want the user to rely on the system to capture the input, but not all input is immediately submitted because you are using **Submit Throttling** or **Explicit Submission**. THEREFORE, **provide hints that indicate what's synchronised and what's pending**. For instance, use a different background colour on text fields. This is important if you are using Explicit Submission or Throttling with a long period.

* Example: [Manoloweb's wiki-like demo](http://www.ideasfreelance.com/lab/instant_edit/) tells you when the edit has been submitted (although is possibly buggy as the message is always there?). (Note: Since web forms were born, many heads and fists have been banged against keyboards after information was lost to timeouts and shutdowns. AJAX is capable of solving this problem, and this pattern is part of the solution.)
</span>

## Interaction Patterns

Nothing new here. All have been available in desktop GUIs and some in non-AJAX DHTML too. This is really just a catalogue of interaction styles that are becoming common idioms in AJAX applications and can benefit from XMLHttpRequest-driven interaction.

<span class="pattern">
**Drag-and-drop** e.g. [This demo](http://www.walterzorn.com/dragdrop/dragdrop_e.htm)
</span>

<span class="pattern">
**Popup data input**
</span>

<span class="pattern">
**Popup information**
</span>

<span class="pattern">
**Highlighting** e.g. [A9's customisation feature](http://a9.com) highlights search plugins you select them.
</span>

<span class="pattern">
**Drilldown** e.g. [Betfair's Sidebar Menu](http://betfair.com).
</span>


<span class="pattern">
**Auto-Completion** Most famously, [Google Suggest](http://www.google.com/webhp?complete=1&hl=en).
</span>


## Coding Patterns

<span class="pattern">
**Browser-Agnostic Components** You want to make the system interactive with sophisticated DHTML, but portability can suffer. THEREFORE, **encapsulate units of DHTML activity into  browser-agnostic components**. A "component" may simply be a Javascript function with a bunch of if-statements, or a factory in an Abstract Factory hierarchy, or a server-side, Javascript generation object.
</span><span>

</span><span class="pattern">
**Server-Side Code Generation** You want to make the system interactive with sophisticated DHTML, but sophisticated DHTML can be difficult. THEREFORE, **use a server-side framework to generate the HTML and associated Javascript**. Note that this pattern will become more useful as frameworks emerge.
</span>

## Further Issues

... which will emerge as patterns.

* RESTful architecture and treating server requests as API calls. There's a lot of scope for XMLHttpRequest to be dealing with a generic, public, API. For instance, it didn't take long before Google Maps had been recruited as a geographical API.
* The "X" in AJAX. How should the response be structured?
* Collaborative applications. How to deal with merges, pessimistic/optimistic locking, etc.

## Your Thoughts?

I'm interested to hear what people think. Leave a comment or send an email to michael@mahemoff.com.