---
id: 278
title: 'SAG Ajax Patterns Review 3 &#8211; Call Tracking, Distributed Events, On-Demand Javascript, XML Data Island, Browser-Side Templating'
date: 2006-03-06T20:00:59+00:00
author: admin
layout: post
guid: http://www.softwareas.com/sag-ajax-patterns-review-3-call-tracking-distributed-events-on-demand-javascript-xml-data-island-browser-side-templating
permalink: /sag-ajax-patterns-review-3-call-tracking-distributed-events-on-demand-javascript-xml-data-island-browser-side-templating-2/
enclosure:
  - |
    http://brain.cs.uiuc.edu/SAG/2006-02-20-Ajax.mp3
    80318592
    audio/mpeg
dsq_thread_id:
  - "375270123"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Events
  - Javascript
  - Links
  - Patterns
  - Review
  - SAG
  - Templating
  - Workshop
  - XSLT
---
<a href="http://wiki.cs.uiuc.edu/SAG"><img style="text-align: right; margin: 8px; float: right;" src="http://img234.imageshack.us/img234/966/illinois3ag.png"/></a>

Following from <a href="http://www.softwareas.com/sag-ajax-patterns-review-1">previous</a> <a href="http://www.softwareas.com/sag-ajax-patterns-review-2-user-action-scheduling-web-service-rest-rpc">posts</a>, here's my notes from the third SAG (Uni. of Illinois CS Dept) workshop/discussion on the <a href="http://ajaxpatterns.org">Ajax Patterns</a>. See the <a href="http://www.softwareas.com/sag-ajax-patterns-review-1">initial post</a> for a background on this series.

Note that there was a "2.5"th workshop on HTML Response, JSON Message, XML Message, etc - it happened, but there's no audio, so I decided to skip it wrt the numbering (the present workshop is really Workshop 4).

<div style="both:clear;">&nbsp;</div>

<b>[Feb-20-2006 Third Ajax Patterns Discussion](http://brain.cs.uiuc.edu/SAG/2006-02-20-Ajax.mp3)</b>
<pre>
============================================================
0:00

Use the "hidden version" versus the wiki
  [MM Guys, definitely the
  hidden version - the wiki more or less stopped a few months
  ago.]

Mention of O'Reilly Rough Cuts
  - Takes a while to make something ready, do you want to deny
    people the advantage of seeing it?

5:00 Intros
============================================================
5:30 Call Tracking

  [MM btw On the wiki, this was the first full pattern I wrote
  and it's pretty awful. Virtually rewrote it for the book. (The
  book content should eventually find its way back to the wiki,
  but maybe something more like the book format, with Wizlite for
  annotation.)]

XMLHttpRequest Call didn't address the bigger picture Call
tracking highlights the async nature of calls - several ways to
track it.  Hand-drawn, crude, diagrams.  
[MM These diags are mockups for the O'Reilly illustrators] Could
have global XHR object - but then limiting multi-processing Is
this pattern worried about resources or reliability?
  - More about
    [TODO Clarify it's about Call Tracking.] From the wiki
    version, seems like resources etc. Ambiguous.

11:00 When start thinking abt async communication, can think
about reflecting on the message. (??)

============================================================
12:00 Distributed Events

Fits quite well with Call Tracking
  [TODO Check Related Patterns sections, add refs?]

Single object/entity might have interdependencies

Clear that it's like an Ajax version of publish-subscribe
  - "Distributed" name confusing, "terrible".
  - Sounds like multiple servers (no).
  - Using patterns like Observer, a different name referring to
    the same thing.
  - But he's focusing on the fact that the events are
    distributed. ie in Java usually listeners are all in the same
    ?space.
  - Yeah it's kind of distr'd events, but the problem doesn't fit
    in with it.

Solution didn't seem to get into the details. Focus went back and
    forth between events and.
    [TODO Observer pattern sidebar]

Interesting, the problem is a really different context. There's
no vocab for that sort of thing, he's trying to create a
vocabulary for it with this pattern.
- Except that in MS case it's transparently distributed. Hook
  docs together, doesn't matter if docs are on same machine or
  not. Built into that (platform). Probably slower than JS.
  People have been building distr'd events systems for a long
  time. Interesting that it's become a big part of these JS
  systems.
- So maybe problem/forces should say more about the complexity of
  the communication

19:00 browser-to-browser is *not* distrib'd.
    [TODO Clarify that it's the same browser.]
  - Last line "should be clear ...": Using a generic interface
    rather than making a specific interface. Could have model
    object with a list of views. Instead, we say the model has a
    list of dependents
      - Well yes, it's another level of indirection, but could
        have implemented update as a list of views. But the main
        thing is, we have a generic interface - you don't know if
        the dependents are views and what they'll do with it. If
        you know they're views and you call redisplay(), you'll
        know they'll redisplay.
      - Had the same feeling - less about extra layer of
        intermediation and more about the fact it's generic.
      - [TODO Reword]
  - Examples: APIs where there's a central mediator. Java
    listeners don't have a central controller, every event
    listener has its own
    [TODO Decision - central manager versus Java-style autonomous
    where each object maintains its own listeners. (See below.)]
  - Decisions: History or state. cf Memento pattern
    [TODO Ref Mememto (or sidebar)]

Enjoyed this discussion. Issues about reflection or whether
interfaces are generic to the problem you're solving. As the
event mechanism becomes more complex, tend to genericise. The
event handling becomes the focus, the architectural locus of
these dist'd environments. Temptation to overload the event
mechanism - the idea of reflection comes in, interesting that we
don't have the vocab to talk about it.

Tradeoffs - "better solution" by adding a layer of indirection.
But that comes at a cost.

I think the heart of this pattern is "something changes,
      something then notified". Key is for Observer, should be
      named after what happened to the subject. If you have a
      system where you're calling your observers to go do
      something ... (different type of events). Events are always
      events relative to some subject, whereas if going to have
      some central repo with dictionary mapping subjects to
      listeners.  Actually a fairly minor issue, but seems bigger
      because not addressed.  As events get more complex, tend to
      centralise it
      [TODO Also depends on sophistication of inheritance and
      delegation mechannisms ... not so great in JS, which pushes
      toward centralising]

33:10 Observer mistakes: Forget to (un)register observer, forget
      to notify observer, forget to declare observer's handler.
      Some mistakes easier to catch than others, for me the ones
      that take longer are when I forgot to register it, esp if
      only in some certain conditions.  From HotDraw, learned it
      doesn't pay to try to be efficient. e.g. Drag figure around
      a screen - must redisplay, therefore must be real fast,
      therefore didn't use observer. So easy to make mistakes
      when mixing those mechanisms (observer and direct call).
      Became a lot easier when committed to using observer for
      everything.
      [TODO Mention this - tip:]

There's a lot you could say about it, not sure author wants to
      say it.  Good purpose: How to convert distr'd events into
      that style. Can see a lot of people doing it the stupid way
      - each display element asking the server if something's
        changed.
        [TODO Flag this risk, probly in Decision about central
        management?]

Code example: Show picture (e.g. interaction diagram)
      [TODO Diagram]

============================================================
38:45 On-Demand Javascript

Just-In-Time JS Not convinced of author's motivation for this.
Would have to be huge amount of JS to worry about it - it's
nothing compared to an image. But I was excited about it for
other reasons, could have dynamic behaviour depending on the
user/context.
[TODO Mention how images are different, they load in parallel and
user can begin interacting beforehand. Can't say same about JS.]
[TODO Emphasise the "behaviour messages" idea as well.]

Need to give performance reasons, could do with an eg in 2-3
sentences Also useful for cross-domain.  "Conventionally best
practice has been to include JS unobtrusively"
[TODO Reword/elaborate if nec Maybe "best practice *is* ..."]

Should have a pattern for modularising your system
[TODO More background info on this, if not separate pattern.]

Near the end of the Solution Variant: Question - What does it
  mean to add new members to the DOM?
  [TODO Clarify ie that nothing will actually happen.] Javascript
  Response - Reword to "Behaviour Message"

Didn't feel that I knew how to do it. Got the big picture, but
not the details, even though lots of pointers. If author wants me
to implement it just by reading the pattern, needs more details.
  - But I never feel like I can do anything unless I try it.
    [TODO Check (the book version has updated this, check that).]

Interesting if browsers could do this automatically.  Cache JS.
[MM Caching addressed in latest book version.]

Question on debugging: What if run eval(js) - if you look at src
for the original page, it won't be there. How will you find those
definitions when you're in the browser? That could be a good
reason not to use it.
[TODO Discuss Venkmann-handling (should work ok).]

==============================================================================
55:30 XML Data Island

Have a group of data you want to do something with - bring the
XML in, display the table etc from that, and you still have the
data.

What's the motivation of having it in XML?
  - They do say that - "could have a custom data format" etc.

Interesting. Stick an entire chunk of XML, which is gibberish to
the HTML, but can still use it.

"Even without these browser-specific technologies ...", so the
author thinks XSLT goes along with XML Data Island.
  - Then you do get this agreed-upon standard for doing these
    transformations.
  - HTML has a schema.
      - Ah but there's this special XML tag. Best thing is for
        the browser to ignore it - they can all ignore it in a
        portable way. (Laughter.)
      - Some people here speak other languages - we're all used
        to hearing a language we don't understand and we all
        ignore it - common human reaction, and somehow our
        programming languages don't do it. Only thing that's
        advanced enough to ignore things it doesn't understand is
        HTML.
      - Ajax is defiantly utilitarian - unrelentingly ugly and
        people just plow ahead. One thing now is that org's like
        Google can pay people to plough through the ugliness -
        crud to deal with, browser dependencies

============================================================
1:05 This pattern answers why using XML. Ajax apps so dynamic,
talking to the server all the time.
      - With HTML, could convert on the server
        [TODO Why not server-side XSLT]
      - Mentions you can offload work
      - Don't want the GUI to be hard-coded into the server.
        Story is weather info - just has to tweak the XSLT -
        doesn't change the XML coming from the weather place.
        Your portal can display it different from anyone else.
      - Fits with web services
      - cf Stylesheets
        [TODO Good to have links to tutorials on XSLT. Chiliplop
        pattern language (?) Book on XML patterns, never
        finished. On website.]

============================================================
1:12:30 Browser-Side Templating

    Didn't see any templates I really liked, even though should
    be do-able.  Authors thinking it makes life easier for web
    developers, I don't know.
      - My guess is that it makes life easier ... because half of
        them are below average, below-average programmers like
        when you can cut-and-paste etc
        [MM Surprised it's seen as a cut-and-paste technique -
        really just a means of separating presentation from
        logic.]
      - With JSP etc, can still let a web designer work on the
        template
        [TODO Explain why - ie to keep the HTML dependence in the
        web tier]
</pre>