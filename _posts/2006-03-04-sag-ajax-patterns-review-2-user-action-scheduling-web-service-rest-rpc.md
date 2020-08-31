---
id: 276
title: 'SAG Ajax Patterns Review 2 &#8211; User Action, Scheduling, Web Service, REST, RPC'
date: 2006-03-04T03:00:00+00:00
author: admin
layout: post
guid: http://www.softwareas.com/sag-ajax-patterns-review-2-user-action-scheduling-web-service-rest-rpc
permalink: /sag-ajax-patterns-review-2-user-action-scheduling-web-service-rest-rpc/
enclosure:
  - |
    http://brain.cs.uiuc.edu/SAG/2006-02-06-Ajax.mp3
    80224384
    audio/mpeg
  - |
    http://brain.cs.uiuc.edu/SAG/2006-02-06-Ajax.mp3
    80224384
    audio/mpeg
dsq_thread_id:
  - "375572805"
  - "375572805"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Javascript
  - Links
  - Patterns
  - REST
  - Review
  - RPC
  - SAG
  - Web Services
  - Workshop
---
<a href="http://wiki.cs.uiuc.edu/SAG"><img style="margin: 8px; text-align: right; float: right" src="http://img234.imageshack.us/img234/966/illinois3ag.png" /></a>

Following from the previous post, here's my notes from the second SAG workshop/discussion on the <a href="http://ajaxpatterns.org">Ajax Patterns</a>. See the earliest post for a background on this series.

<strong>[Feb-2-2006 Second Ajax Patterns Discussion](http://brain.cs.uiuc.edu/SAG/2006-02-06-Ajax.mp3)</strong>

"We should set up wizlite "sag" group for annotations" [MM For the benefit of others, the online book draft version uses Alex Kirk's Wizlite.]
Wizlite - is it Ajax?  [MM Yes, Alex Kirk's a prolific Ajax developer and writer]

Wizlite - can you trust the data on all these things to stay online [MM Backup solutions like openonomy, part of the argument with these Web 2.0 things is they host it, but you own the data, so you can in theory point a backup service to it and at least you'll always have the raw data. As for privacy, not much you can say about that (although, in theory, Ajax lets you host encrypted content- see the Host-Proof Hosting pattern).  Also, some free content is available, then removed.

Maybe AjaxPatterns.org will go down when the book is published [MM I know it was a joke, but just to let you know, won'tâ€ happen. It's a CC license, and a big factor in going with O'Reilly was being able to keep the wiki online before, during, and after. Interestingly, O'Reilly didn't have the Rough Cuts program going at the time, but they presumably had been planning it.]

Author had some auditory issues, need to fix that.  [MM Thanks,
this mp3 worked out better. The first one was fine too once I
listened to it with better earphones. Given the quality of my
own podcasts, I certainly can't be a critic here. BTW I think
it would be great if the SAG talks were actually linked from a
feed. To me, this is the best kind of podcast you can get -
it's zero effort -  a meeting that would have happened anyway.
(Unlike, say, me rambling about Ajax, which is not something I
normally do spontaneously)]

=======================================================

10:50 User Action

So what is the User Action pattern?
- What's the proper way of handling user actions?
- "User Action" is more of a problem than a solution. More
Event Handler or Callback. Names are typically solutions.
Or does a JS programmer call it that? [MM No].
- Rather call it Listener than Event Handler if that has a
narrower connotation.
- Depends on what people really call it.
- But better names come along too, e.g. "Ajax".
- Listener is kind of Java-ish, and JS and Java don't have
much in common other than the name.
- The "Java" in "Javascript" name was marketing-driven, a
misnomer.  [TODO Mention ECMAScript/Javascript
distinction in conventions section]
- => Suggestion to author for rename

Implies you're not going to see that event loop, it's
invisible, it's probably more in the virtual machine.
- If doing distr'd programming, end up with lots of loops.
Difficult to integrate different packages. If all buried
inside the language, could be better because no
incompatibilities, but could be worse because it's
invisible.
- So events are part of this language.  [MM Yes, part of the
browser's DOM implementation]

OK, issues
- Not specific to this pattern, but author discusses
incompat's between IE and Firefox. Should be some
mentioning about this.  [TODO Check pattern mentions libs
and deals with this in general terms.  Note that intro will
discuss how incompats are handled. Mostly, the answer is
"Use a library" and that it's beyond the scope of this book
- refer to a JS/DOM book instead. Also, note that I only
address IE and Firefox directly.]
- Prototype library deals with this.
- IE7 uses XHR natively. [MM True, though not a huge deal,
before you just needed a factory function. The bigger
question is whether they behave the same]
- Code - redefine the event handler - is that common?
Wouldn't normally do that.  [TODO Indicate this is rare,
possibly scrap the Decision. Note: This is indeed somewhat
rare]

Could people write a User Action
- Just showed onMessageMouseOut or whatever, needs to at
least show the outline of the function [TODO I think the
request here is to show the signature of onclick,
onkeypress, etc. Except they're all the same - onclick(ev),
onkeypress(ev), etc. Need to clarify this in the solution]
- Interesting that not compatible across all platform
- Couldn't you abstract out differences between events
[TODO I thought that was mentioned, including the
quirksblog et al contest, check it]
- Interesting discussion on p5 about dynamically ..
- Upon seeing that, and if he feels that way, scoring
this as a variant of Observer would be an interesting
way to go.
- That section was a bit confusing. Third parameter was
confusing.
- How often do you need to have >1 event handler? Not
very often.  And can always have a composite handler.
[TODO Mention that.]
- JS event mechanism involving strings e.g. "onclick" for the
event handler. Neat but refactoring side of me starts to
worry.  [MM Could say the same about onclick ... in JS
x.onclick is equivalent to x["onclick"].]

=====================================================

29:00 Scheduling

What is it?
- As the author puts it, running something at a time in the
future or repeatedly.
- Another use of event handling. And that's one reason why
"User Action" is better than "Event Handling" [MM That's
basically the rationale I used, could still be "UI
Events"]
- The vocab is tricky because the overall JS vocab and
ideas are still emerging.
- Maybe some background on JS event handling is available
in the earlier section.  [TODO No it's not. A little in
the tutorial but no. Needs sidebar perhaps.]
- Is the author assuming JS?  [MM Assuming basic
knowledge. I suspect most readers have done a little
hacking with it, the kind that was used in pre-Ajax
style web development.]
- Seems like it's assumed.
- But sometimes seems to assume reader doesn't know
anything about JS.  [MM Unfortunately, Ajax is so
all-encompassing that it's a tricky issue, and the
group of people who could benefit from these patterns
is also quite wide. So it's been a juggling act, but
I'm really assuming some basic web development, and
not necessarily any general GUI development (ie there
are plenty of people who've programmed PHP for 5+
yrs, maybe since high school, and have never done
anything like Swing).]
- Only has example of one-off. Not for repeated event.
[TODO Check that. (Solution itself includes that, but
maybe reference it from examples, or reference other
examples that use it eg Live Search).]
- I thought it (JS) was supposed to be object-oriented
- As much as it's like "Java".
- I saw that JS is a prototype-like language in the Self
tradition.  [MM True. Each object has a mutable
"prototype" property. We still need to work out how to
fully harness it]
- Could also have network events [TODO Sidebar: Also
point out other events: XHR, onload/onunload]
- Worth mentioning that the timers are not really timers,
I'm not going to run my pace-maker using these timers
[TODO Precision of timer]

=====================================================
41:00 Web Service

Author provided it even though not on the wiki (as with Ajax
App)

Quite short and for being an important pattern, it didn't
seem to be very detailed. So what is Web Service?
- Just seems real simple, what the Ajax .. is going to call
on the server.
- Uses HTTP protocol to pass parameters and bring back
data. Could use SOAP, whatever.
- It's a Context, not a pattern. I'm not sure how serious I
am about that, but ...
- Problem: What will the Ajax App call on the Server.
- Important to have a web service, just not sure (??if
need it as a pattern).
- Name is ambiguous (because of SOAP etc)
- Well that's what there are other patterns for eg REST
and RPC.
- Part of the problem is there isn't much content to a web
service. The hard part is working out what all the
messages are, what to expose, etc.
- Even when CORBA came out, we felt like, this is old-hat,
just trying to standardise what we've been doing, etc.
- Want to have layers - CORBA, COM, components, Web Service
is just the latest in a long line. SUN-RPC (early 80s)
was already a standard.
- This not only doesn't tell you how to do these hard
issues, but doesn't.... I would like to see something
like: Just because decided to do web service, problems
aren't over. Only just begun. Have to decide on (etc).
People want freedom from choice. One reason people like
SOAP, REST, etc.  [TODO Mention that]
- Also, why did web services arise that way? Why not a
custom service on port 1065? Why HTTP?  [TODO Sidebar?
Forces?]

=====================================================
53:10 RESTFul Service

- Main distinuishing factor bn REST and RPC: REST uses
standard keywords for communicating to services. He has
interesting anecdote on Google (Accelerator).
- The idea is if everyone starts following REST,
documentation is minimal.
- "Motivating REST" - He does say important things like
there are going to be web crawlers, caches, proxies, etc.
So how can you make sure people's assumptions are met ...
[TODO Check this is emphasised enough] And I think that's
a big part of REST.  [TODO Use the browser as an example,
ie type URL makes it perform a GET request]

What do you wish you had in here?
- No (I didn't understand REST from this).
- REST = Non-SOAP procedure call.
- I've heard people say you can use SOAP in a REST-like
way [MM Yes, mentioned in "RPC Call" pattern and also
in the RPC discussion in the REST solution]
- How is this different from a standard form submission?
[TODO Sidebar or explanation comparing to std web call?
e.g. REST usually returns XML]
- Normal web form submission is REST automatically,
although one of the things is you want POST to be
idempotent. So when you POST, you've made a new object.
ie Put an ID on the form, so when you POST it says
"I've already seen this. You've sent me this order
already." So won't put in two orders.
- Okay, I was going to ask this ... using the URL as a
piece of the environment?
- No, not the URL. Cannot do it with the URL. The
URL tells you the object that you're posting.
- Points to examples in Solution. But these aren't
RESTful [TODO *** Make it a lot clearer that
these these match examples aren't necessarily
RESTful!!! I think these might have set the stage
for general REST confusion!]
- Football service [MM Incidentally it's Aussie
rules :->]
- Matches==Games [TODO Change to "game", good
enough for everyone]
- I think REST would be good for CRUD, but not sure for
transactions.
- Well, TX's are more difficult. Have to make an
object that represents the TX, and that's how
businesses work. "I sent you the purchase order,
etc".  [TODO Be more clear on this]
- Author should describe something outside CRUD.
[TODO It's already there in later sections, but
maybe discuss it upfront?]
- Was looking forward to learning about REST, but still
left wanting more.
- The important people here are those who don't
know REST, hence probably needs more content even
though it's already long.  [TODO Consider what to
add/change]
- TODO A REST and RPC FAQ Sidebar
- e.g. Can RPC be RESTful?

=====================================================
1:13:55 RPC Service

- Package up params, unwrap etc. There's a bunch of ways to
do it and he talks about them.
- Call-By-Reference. URLs can be your references [TODO
Mention that]
- With REST. A lot of things you could say. e.g. Make up
all the arguments in the URL. But if you have side
effects, that doesn't work.  The side effect operations
that aren't idempotent, e.g if you're doing SOAP, args
will be passed in the POST message, so the URL isn't
really a resource.
- Pretending you can treat the world as a bundle of RPCs,
have to cope with lack of availability, errors, etc,
which make RPC unreliable.
- Which is why REST is successful. What if someone
moves a page?
- Would be nice if RPC was possible, but it's just not.

1:22 Next time: Patterns after RPC Service?