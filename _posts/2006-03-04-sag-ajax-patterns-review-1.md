---
id: 275
title: 'SAG Ajax Patterns Review 1 &#8211; XHR Call, IFrame Call, HTTP Streaming'
date: 2006-03-04T02:51:40+00:00
author: admin
layout: post
guid: http://www.softwareas.com/sag-ajax-patterns-review-1
permalink: /sag-ajax-patterns-review-1/
enclosure:
  - |
    http://brain.cs.uiuc.edu/SAG/2006-01-30-Ajax.mp3
    81625216
    audio/mpeg
dsq_thread_id:
  - "382804646"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - IFrame
  - Links
  - Review
  - SAG
  - Streaming
  - Workshop
  - XMLHttpRequest
---
<a href="http://wiki.cs.uiuc.edu/SAG"><img style="text-align: right; margin: 8px; float: right;" src="http://img234.imageshack.us/img234/966/illinois3ag.png"/></a>

A little while back, I mentioned that some people in the patterns community <a href="http://www.softwareas.com/ajax-patterns-in-the-pattern-community-radar">have been noticing</a> the Ajax Patterns. In particular, **there have been a series of discussions about the patterns by the <a href="http://wiki.cs.uiuc.edu/SAG">Software Architecture Group</a> in the <a href="http://www.cs.uiuc.edu/">University of Illinois Computer Science Dept</a>** (home of Netscape forerunner Mosaic btw). The SAG is led by <a href="http://st-www.cs.uiuc.edu/users/johnson/">Ralph Johnson</a> (Gang Of Four "Design Patterns" author) and <a href="http://wiki.cs.uiuc.edu/SAG/SAG+members">the group</a> also includes <a href="http://www.laputan.org/">Brian Foote</a>, who <a href="http://www.laputan.org/catfish/archives/000139.html">blogged about Ajax as a pattern earlier on</a> and has kindly been keeping me updated on <a href="http://brain.cs.uiuc.edu/SAG/">the MP3s emerging from these discussions</a>.

The feedback has been very helpful and I've been able to incorporate it in time for the physical publication - thanks again to everyone in the group.

While listening to the audio, I've been taking notes and writing some comments. With the permission of Ralph and Brian, **I'm going to be posting these, each discussion as a separate post. It's an opportunity to see how a group of very intelligent people without much Ajax experience respond to Ajax and the Ajax patterns.** You'll notice two conventions here:  "TODO" is a note to myself that some action needs to be taken. "MM" signals my ideas, views, and comments back to the group.

<b>[Jan-30-2006 First Ajax Patterns Discussion](http://brain.cs.uiuc.edu/SAG/2006-01-30-Ajax.mp3)</b>

30/1/2006 Ajax Workshop
<pre>
===============================================================
9:45 XMLHttpRequest Call

What it's about.
  - Probably missing in old browsers if you can't use Ajax on
    them.
  - Remote call to server without refreshing a whole page.
  - I assumed in JS you can open a socket, you could have done
    this yourself.
    - Depends on what the browser provides. But not
      cross-browser.  [TODO Mention HTTP restriction and what JS
      can do, cf Richer Plugin]
    - Ironically, because JS isn't general-purpose (due to
      security), it's wound up being a better citizen. Also
      because it was kind of low-brow, everyone kind of ignored
      it.
  - The big idea is this is a way to call the server.

Interesting characteristic of XHR:
  - Asynchronous
  - Built-in security (originating server)

Did you find this pattern easy to understand?
  - One thing that troubles me (not particular to this pattern),
    pretty soon the code becomes spaghetti-like. Nd good patterns
    on how to manage code.  [MM Agree, we need a JS patterns
    book! That's not the aim here, the book will make that
    explicit].
    - Part of the problem here is JS itself.
  - Haven't seen the word "simple" "elegant" or "pretty" to
    describe JS architect. This is a Rube Goldberg solution,
    duct-tape ... at it's best.  [MM Sort of true, but there's a
    lot that can be done to improve it]
    - There are libraries that help. (AjaxCaller, Prototype).

Writing here, even though it doesn't address these problems,
could understand/follow it?
  - I don't like the Problems section. "How can the browser
    communicate with the server?" But this pattern is more
    specific than server communication.  The next 1-2 patterns
    have the same problem.
      - But the problem might be the same, but different
        Solution. What I dislike is the forces are also the same.
        How does it mitigate the forces? Maybe there should be
        some different forces.
      - Only difference between IFrame and XHR is only restricted
        to same host, so maybe okay other than that.  [MM
        Actually, even this difference doesn't exist, since you
        can't read a remote IFrame's content] [TODO Possibly
        update forces to be different, back-reflect the solution]

22:30 Doesn't say anything about being asynchronous at the start
  - Ajax should be highly responsive. Distributed system, so you
    want to minimise communications. ie Must be asynchronous
    [TODO Revise forces. HOWEVER, note that XHR doesn't have to
    be async.]
  - "Conventional means ... slow." He's trying to rule out
    Solutions, before we get to the solution.  [MM This sort of
    goes against the previous suggestion that IFrame and XHR need
    different Forces. Maybe suggests different people have
    different views on this issue of the forces.] Doesn't so much
    talk about the forces as take potshots at existing solutions.
    [MM This is a fair point, more prevalent in the initial
    patterns as they're arising as a reaction to conventional web
    dev, but it's true you don't have to formulate them that
    way.]

26:30 It's a long pattern, is that okay?
  - Yes, longer than all the others, problem if all patterns were
    this long, but given it's so core to Ajax, it's fine.
  - Length is fine, but a lot of code there.
    - I would like more examples of the old way of doing things.
      [Covered in the Anagrams tutorial, perhaps reference it]
    - The general idea is if you have a big object and only small
      things change at a time, then you keep going back to the
      server and grabbing small bits of it. I think of Google
      Maps.
  - Pattern could be shorter if PHP wasn't written.
    - So you'd like *less* example code, others want more.
    - It's a Chimera/Frankenstein ie PHP (or whatever serverside)
      on the one side, and even JS is a kind of Frankenstein
      language. So it's important to have the PHP, reminds me
      that's the game I'm playing. I didn't mind it, seeing all
      the pieces together reminds you we're receiving small
      chunks etc.
    - The pattern is really introducing XHR, not how to use it.
      - Disagree with people who are trying to call everything a
        pattern.
      - Well, these particular patterns are what he calls
        foundational. He says they're not really patterns,
        they're just how the technology works.
      - I know what you're saying about that, and it bugs me too,
        but I've been trying to come up with a rationalisation
        for admitting that this kind of design exposition is a
        contribution to our software architecture literature ...
        and if designs recur, if a lot of people come up with the
        same solution to a problem ... my mind cries out to keep
        distinct from Visitor and ... Composite, but I don't have
        the vocab to keep them distinct, and I want to maintain
        this notion that the patterns community is talking about
        good ideas that keep coming up over and over that we
        haven't come up with ourselves ... true, it's a different
        kind of discussion from the GoF, without having
        disclaimer kind of nags at me [MM Agree wholeheartedly,
        why I've sounded a bit apologetic describing these as
        patterns, but they just fit into the overall language
        well.  See earlier blog post.] [TODO Needs better
        "disclaimer" in the book]
    - So then what are the patterns around XHR?
      - Event handling, Asynchronous call
      - Lots of people dealing with SOA, problems s.a. async
        smell the same but with different names [MM Later
        patterns, e.g. Distr'd events]
      - Error detection
      - Invesion-of-control/DepInj/Observers. People patternising
        closures.  There's an aspect of dealing with callbacks.
        Callbacks are part of the discussion here, and that's an
        idea that comes up here.
      - Feedback from the call. Or using poll. Fire-and-forget.
        Typical remote invocation styles: What does XHR do?
      - In JS: Callbacks used here (XHR), also used for user
        interops. We want to follow flow-of-control, but if
        everything is event handlers, hard to follow. (ie JS hard
        to follow because of this style.) A lot of the time,
        "callbacks" are basically continuations. It's a general
        pattern discussion we could have.

41:30 Real-World Examples and Code.
  - These systems are not thoroughly responsive as claimed.
    Google Suggest surprisingly fast. Others like Backpackit and
    Kiko not.  [MM See perf optimisation, also comments in HTML
    Message, etc. Alex Kirk mentioned Kiko a while ago as a
    problem due to too much browser-side rendering.]
  - Need to avoid too many requests
  - Curious didn't mention the most famous examples (Google
    Suggest etc) Maybe can't see the code. But it's JS, have to
    be able to. But maybe unclear.  [MM Yes, obfuscated. Also,
    tried to avoid the cliche references too much, they're
    mentioned elsewhere]
  - Discussion about mint stats package, security issues in
    uploading data.
    - Next, ways of telling your web browser what to report back.
    - If trying to keep people from attacking you. It's
      interesting to me.
    - Applets got crucified for some of the security problems
      that JS has.  People moved on from panicking about them,
      but got away with it because browser wars finished etc.

===============================================================
49:00 IFrame Call
  - Poor Man's version of the previous one.
  - More like a hack
  - What can you do with one that you can't do with the other?
    XHR and not with IFr?
    - I only know the other way round...IFrame is more compat
      with older browsers.
    - Long discussion about relative benefits etc.
    - Comment about Google using IFrame. Not sure if it's true as
      you can zoom in.[TODO More specific about how it's being
      used. (I think book version already does that)]
    - IFrame Call doesn't talk about hidden frames.  [MM XHR
      Pattern alternatives has a detailed comparison)] [TODO XHR
      comparison should briefly explain *how* the two are diff,
      not just compare the benefits]
    - IFrame has no timeout function. (But could fake this using
      polling)
    - Calls IFrame a hack ... Pot calling the kettle black, since
      Ajax itself is sort of a hack. Is it bad just because it's
      old?  [MM Again, comes down to the comparison. XHR is a
      more intention-based, intuitive, API, although it's true
      that you won't care about that because you should use a
      wrapper lib anyway. Better argument is the extra
      functionality such as call tracking.]
    - Would like better explanation on what's so bad about
      IFrames.  [TODO Include x-reference in IFrame Solution.
      Also mention the portable wrappers in the Solution, ie you
      shouldn't actually care/know which you're using is the more
      pertinent issue here.]
    - I'm feeling historical. The room we used to sit in is the
      room where the original Mosaic web browser developers sat.
      Continuously astonished in the web industry, using things
      that in ways they weren't invented for. Go down this list,
      frames, tables ...  Ungodly mess, but really impressed,
      poster child for pragmatism and "worse is better".  IFrame
      is a typical example.
  - I didn't get any feel on whether I would use one or the
    other.
  - Intrigued by the history of JS. Knowing that IFrame predated
    XHR because features that made it easier to do the second
    came along in 2003. Whether it needs to be here, not sure.
    [TODO Sidebar?]

===============================================================
49:00 HTTP Streaming

    Is it competition for the other two?  
      - Different problem (push/streaming)
      - "How can the browser communicate with the server?" Same
        problem as the other two.
        - I don't know, it turns the table. Little pattern device
          of using the same problem with different solutions may
          be okay here. Here, the forces would be different.
          Could make the case for having the same problem.  [TODO
          Change the problem statement, just enough to make it a
          little different from previous two.]

    What would make you choose this over the others?
      - Changes coming from lots of other sources, not just the
        client.
      - e.g. Chat system.
      - I don't want to do this. Don't want to grow the system
        ...
        - But scaleability is oversold. You'll never be like
          EBay, don't need to scale up like that.  [TODO Good
          point, mention in the pattern.]
        - Our wiki - 4-5 hits per second - can handle that, but
          not scaleable.  Wikipedia is not a wiki in that sense,
          pages don't change because I believe something like 90%
          of all edits are done by 200 people, these are official
          wikipedia authors. Specific process.
        - Doesn't fit into proxies. Caching etc doesn't ddeal
          with longer responses.

    Long refactoring illustration here. Do the others have one?
      - Streaming wiki demo.
      - Seemed nice to refactor in this way.
      - The group is looking at the live version on the web -
        "There's about a half dozen laptops in it for the
        author's information". It worked.  [MM Phew]

===============================================================
1:20
    - I didn't get the feel of which one to use.
      - Was hidden in the Alternatives section [MM TODO Emphasise
        this in the partintro, maybe in the solutions]

======
Next time: Different patterns
    - Problem with web version [MM Incidentally, the wiki
      publishing hasn't worked out ideally, didn't get the full
      benefit as I didn't open up the wiki (and still haven't due
      to spam). Ideally would have better PS format. (Blogged
      about printing from the web a yr ago as it happens.)]
    - Being on the web doesn't seem to affect (ie drop) sales.
      [MM We'll soon find out...:-)]
</pre>
