---
id: 337
title: Rails, Selfishness, and Opinionated Patterns
date: 2006-08-05T01:32:37+00:00
author: admin
layout: post
guid: http://www.softwareas.com/rails-selfishness-and-opinionated-patterns
permalink: /rails-selfishness-and-opinionated-patterns/
dsq_thread_id:
  - "375573059"
categories:
  - SoftwareDev
tags:
  - DesignPatterns
  - OpinionatedSoftware
  - Patterns
  - Rails
  - Selfishness
---
When people talk about their favourite benefit of Rails over framework X in language Y, they'll usually mention ActiveRecord, Ajax support, etc. But at a deeper level, the thing that really stands out is that Rails is opinonated software. This is where Rails derives its power and agility.

It's pretty well-understood in software that consistency trumps piecemeal optimisation. Consistency comes from opionated software, piecemeal optimisation comes from design-by-committee. By piecemeal optimisation, I'm talking about something that's full of good little chunks of local functionality, but falls apart when you use it because everything works differently.

<img src="http://img205.imageshack.us/img205/9752/whitechesskinghl4.jpg" width="400" height="300"/>

Stated in another way, opinionated software is task-driven, whereas design-by-committee tends to be technology-driven. When DHH says the sky is now red, he's selfishly refactoring things in such a way that he can work more effectively. I was about to slap quotes around "selfishly", but the truth is, it really is a selfish act. And therein lies the benefit - it's often better for me, as an end-developer, to work with a framework that one man (being DHH) has produced for himself than to work with one produced by a committee of agents with a variety of potentially conflicting interests. This, of course, assumes that DHH is talented and that he works on similar things as me.

Caveat: The above is a very crude approximation of the truth which ignores the contributions of many talented core developers, contributors, and feedbackers. And of course, I don't mean selfish in a malicious sense, I mean it in an "enlightened selfishness" sense.

What's particularly interesting about opinionated software is that it mirrors the subjectivity of patterns that has been discussed for years, by Richard Gabriel, Jim Coplien, and others (see <a href="http://www.amazon.com/exec/obidos/tg/detail/-/0195121236?v=glance">Patterns of Software</a>).  While patterns are sometimes thought of as the endpoint of rational, wiki-ideal-like, trial-and-error, they are actually highly subjective. Indeed <a href="http://mahemoff.com/paper/language/">subjectivity is a key distinguishing factor between pattern languages and pattern collections</a>.

<blockquote>
<p>To appreciate the importance of a pattern language, it is necessary to comprehend the subjective basis of pattern languages. Far from being the objective and exhaustive catalogue of ideas they may initially seem, patterns are based heavily on an underlying set of values. They explain how forces are identified and resolved according to certain principles; in doing so, they are encapsulating a particular approach. Alexander identified, valued, and discarded patterns in a process which embodied his own architectural philosophy (Kerth, 1997).</p>
</blockquote>