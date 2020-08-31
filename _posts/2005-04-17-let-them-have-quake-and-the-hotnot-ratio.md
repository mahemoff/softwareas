---
id: 101
title: 'Let Them Have Quake: Bad Programmers are Negative Contributors'
date: 2005-04-17T23:15:37+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=101
permalink: /let-them-have-quake-and-the-hotnot-ratio/
categories:
  - SoftwareDev
---
I just began reading [The Business of Software](http://www.amazon.com/exec/obidos/tg/detail/-/074321580X?v=glance). The intro alludes to that **old adage  about a good programmer being 10-20 times as effective as a bad programmer**. I've heard various numbers for this "Hot/Not" ratio, sometimes 100 is bandied about. I think it's a fine way to convey a pertinent point of software development to non-techies. The figure is obviously arbitrary, so no issue there. I've had the (mis)pleasure of working alongside both ends of this spectrum, and, at least from what I've seen, it all makes sense, as long as you assume the developers are isolated.

Given a small project to work on in isolation, a hotshot hero programmer might be able to produce a high-quality system in a couple of weeks. Meanwhile, the bizarro programmer will spend some time looking things up, and eventually cobble together something vaguely meeting requirements, vaguely compiling, vaguely running, in a few months. Thus validating the 10x theory, or the 100x theory if you're factoring in quality too.

<b>However, the Hot/Not ratio falls down in most projects, because the bad programmer usually works in a team, not in isolation. </b> In agile projects, as well as the industry-standard code-n-fix approach, all code is up for grabs. Agile projects usually promote collective ownership, code-n-fix projects often do promote some idea of direct ownership, but reality usually rears its ugly head and people are forced to read and write others' code. Only in the most rigourous, well-executed, top-down, sequential, design projects can developers really work in isolation. Whether those projects are desirable is beyond the point, the point being that most projects are either agile or code-n-fix or attempts at sequential development which degenerate into the latter. And that being the code, I rest my case that most programmers work in teams.

**In team-based projects, a bad programmer can be every bit as effective as a good programmer, but in the wrong direction. In other words, the same contribution with negative polarity, meaning that the "Hot/Not" ratio is negative. Perhaps -1, -10, who knows? And really, you can have the whole spectrum between those two extremes, which is why the standard "tenfold" figure is really very arbitrary.**

Where the hero can singlehandedly code a system to a higher state, the bizarro hero can drag it down with the flick of a key. By a bad programmer, I'm not just talking about someone who's development experience consists of "Parallel Computation Algorithms in 24 Hours". I'm talking about someone with poor communication skills too. Communication skills are at least as important as technical skills, and I'm assuming we're a little under-par here too.

Specifically, a bad programmer has a negative contribution on a team-based project, because (PC disclaimer: I'm saying "he" for concreteness):

* Subtle bugs get introduced by careless coding. They can take a long time to locate and fix.
* He is not interested, or perhaps not very good at, expressing what he's done to other team members, who may find certain things curiously weird, but for no known reason.
* He is not interested, or perhaps not very good at, listening to other team members, so will trample on their work.
* Other developers constantly have to slow down to give explanations and help in debugging sessions. (It's good to encourage discussion and support, but only if it doesn't become groundhog day, and it should usually happen in both directions.)

Does all that sound like a dampening effect - e.g. one-tenth a good programmer - or a downright damaging effect - the opposite of a good programmer? Yep, the Hot/Not ratio is negative in most projects.

Now, **the agile approach typically says that if all the interventions fail, you ask the person to leave the team. But there's a practical problem: for various organisational reasons, some people must remain on a project even when they are known to have a negative contribution factor**. If the "tenfold" ratio applies, the manager might reason that the bad programmer may as well do his 10% job. But if the negative theory above holds - and I maintain it does - the right thing to do is to sidestep them altogether. **The best thing a manager can do in this situation is to let them have quake.** That is, give them a well-spec'd PC in a corner of the room, a copy of their favourite game, a suitable game controller. And some good headphones. Or, realistically (the quake thing just sounded cool), a little greenfield tool they can develop in isolation from the code base. Alternatively, monitor changes very closely.This brand of sidelining isn't pretty, and let's keep in mind I'm talking about situations where the programmer has already had all the opportunities to pick things up and just wasn't interested. It's a pragmatic way to deal with those awkward situations where a developer really isn't in good shape to touch the source code, but must remain on the project.