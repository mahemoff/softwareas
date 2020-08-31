---
id: 614
title: TiddlyWiki Quiz Plugin
date: 2009-09-11T01:07:21+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=614
permalink: /tiddlywiki-quiz-plugin/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574404"
categories:
  - SoftwareDev
---
<a href="http://tiddlywiki.mahemoff.com/QuizPlugin.html"><img src="http://img.skitch.com/20090911-kq744xf5dx5eas1unrtk96qyw3.jpg"  style="width: 400px;" /></a>

I've produced a Quiz plugin for TiddlyWiki this evening.

<a href="http://tiddlywiki.mahemoff.com/QuizPlugin.html">Quiz plugin and demo here</a>. (And source code in <a href="http://svn.tiddlywiki.org/Trunk/contributors/MichaelMahemoff/plugins/QuizPlugin/">subversion here</a>.)

It's a macro - you just put &lt;&lt;quiz&gt;&gt; in a tiddler somewhere and it will suck in all the question tiddlers, format them to show a quiz, and let the user fill their answers in.

Authoring is pretty simple - you pretty much write each question and its multiple choices out as you'd like the user to see them. The options are just a list. Any options beginning with "*" are wrong, any options beginning with "**" are right.

There's no server-side, so it's very easy to cheat. That's why Joe made Firebug in the first place. Isn't it? No? Actually, this pattern is very much in line with the TiddlyWiki philosophy (and, further back, C2 wiki, where the voting mechanism was just editing a wiki page) - a lightweight solution where people are trusted to do the right thing. Would you use it for entry to medical school? Probably not. But it's good enough for personal drills, and TiddlyWiki is after all a personal sketchbook at heart. Maybe we'll tack on a server-side in the future to lock away the answers properly; but for now, this will do as a proof-of-concept. And besides which, most Java/Flash/Active-X/just-plain-weird corporate training tools probably hide the answers away somewhere in the client anyway. With a little ROT-13 obfuscation, we can achieve the same effect here.

And of course, there's plenty of room for options and different question types too. This works okay as is, but many more possibilities around.

Why did I write this thing?

* Quizzes are tied to the concept of <a href="http://softwareas.com/as-we-may-think-url-trails">URL Trails</a>. It would make perfect sense for the final page of a trail to be a quiz. Or, for a longer trail, for quizzes to appear along the way.
* I was triggered by several hours of "fun" with a mandatory training quiz which, typical of corporate training apps in any big organisation I've ever worked in, went out of its way to break web standards. Perhaps this here quiz plugin will be the embryo of something we can use to help improve training. Again, this relates to trails because trails have an educational flavour to them. At an organisational or project level, it's feasible that the two would be developed as part of the same overall programme.
* Quizzes are something I have <a href="http://softwareas.com/quizr-quizzes-20">a personal interest in</a>.

As an aside, building plugins is *so* much easier with JQuery in the TiddlyWiki core, probably three times as fast .... hurrah for that!

[Updated Sep-15-2009: can reset quiz, shows number of correct options, UI enhancements, internal refactorings]