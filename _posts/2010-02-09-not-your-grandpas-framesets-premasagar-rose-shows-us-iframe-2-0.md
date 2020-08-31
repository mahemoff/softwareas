---
id: 780
title: 'Not Your Grandpa&#8217;s Framesets: Premasagar Rose shows us IFrame 2.0!'
date: 2010-02-09T00:09:12+00:00
author: admin
layout: post
guid: http://softwareas.com/not-your-grandpas-framesets-premasagar-rose-shows-us-iframe-2-0
permalink: /not-your-grandpas-framesets-premasagar-rose-shows-us-iframe-2-0/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "380667457"
categories:
  - SoftwareDev
tags:
  - Ajax
  - IFrame
  - Javascript
  - Web
  - Widgets
---
usual live blogging caveats - spelling errors, messy, etc etc

@premasagar is visiting the Osmoplex today (thanks @jayfresh for arranging it) and is taking us through his work on iframes, widgets, and sandboxing. I've realised we could perhaps be collaborating as my jquery-iframe plugin is so close to his. Different emphases, but much overlap.

[GitHub](http://github.com/premasagar) is where you can see what he's been working on. Basically, this guy is a guru on all things iFrame. In particular, all the quirks around squirting dynamic content into iFrames, as opposed to pointing them elesewhere using "src".

QUOTE OF THE DAY

"sqwidget is my tiddly"

BACKGROUND - THE EMBEDDING PROBLEM

In patternesque speak, the basic problem is:

Problem: You want to embed 3rd party content into another site.

Forces:

* You want the 3rd party content to have its own style
* BUT it will inherit style from the parent page

SOLUTION 1

IFrame

Works great (in fact, I'm using it in my TiddlyWiki playground app, to be documented at some point, and is similarly used in Jon Lister's [TiddlyTemplating](http://iwab.tiddlyspot.com/).

The problem is you sometimes want the widget to jump out of the iframe, e.g. a ligthboxed video. So ...

SOLUTION 2

[CleanSlateCSS](http://code.google.com/p/cleanslatecss/)

Basically a CSS reset, but whereas CSS resets will only handle browser defaults, cleanSlate blats everything! This is exactly the kind of thing I was looking for when <a href="http://groups.google.com/group/tiddlywikidev/browse_thread/thread/53f7c8120a3c3887">I was trying to cancel out tiddlywiki styling</a>. In that case, I was flipping the entire page back and forth, so I could just cheat by removing stylesheets and re-add them. (Prem pointed out there's a "disabled" attribute on style tags - <a href="http://www.w3.org/TR/DOM-Level-2-Style/stylesheets.htm">true</a>, so I should really use this instead, assuming it's portable, which he thinks it is.)

Problems:
- Difficult to maintain CleanSlate library, because new CSS stuff and browser quirks keep coming up
- IE6 and IE7 don't support "inherit", so need CSS expression.
- When using Javascript to interact with CSS style properties, e.g. slideDown(), these will override CleanSlate. The solution is to set the "style" attribute with !important, but it becomes an arms race!
- Doesn't solve iFrame security model

SOLUTION 3

Inject (aka squirt, inject; [summary](http://softwareas.com/injecting-html-into-an-iframe)) content into a fresh iframe.

The content comes from the widget site. The sqwidget library injects it. This resolves the tension with wanting independent CSS on the same page. If the sqwidget library is running on the host page, it could even (potentially) lock down capabilities, i.e. do Caja-style sanitisation.

Sqwidget also does templating, using Resig's micro-templating. (That thing's getting to be very popular; I'm using it myself in Scrumptious via the UnderScoreJS library after @fnd gave us a talk about them.)

Also, prem is playing around with the idea of a div, with custom (data-*) attribute pointing to the third-party URL. You could put inside it "now loading" and then the script tag will pick those things up and load them.

----

Various points:

- for content-squirting into the iframe, you should be setting doctype, otherwise IE will load in.

- worth investigating use of <object> tag