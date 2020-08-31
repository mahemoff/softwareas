---
id: 49
title: 'Source code: String of ASCII or Tree of Goodness?'
date: 2005-01-26T00:29:09+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=46
permalink: /source-code-string-of-ascii-or-tree-of-goodness/
dsq_thread_id:
  - "384542637"
  - "384542637"
categories:
  - SoftwareDev
---
Source code as structure rather than text ... bring it on!

Jon Udell blogs about [The Deep Structure of Code](http://weblog.infoworld.com/udell/2005/01/19.html#a1154). Instead of treating source code as a boring old text file, treat it as a data structure. Then, you can render it however you like it. I was captivated by this idea when I read [this 2003 James Gosling interview about Jackpot](http://www.artima.com/intv/jackpot.html).

Gosling explained that treating programs as structures lets you perform powerful refactorings:

<blockquote>
It's a very different world when a program is an algebraic structure rather than a bag of characters, when you can actually do algebra on programs rather than just swizzling characters around. A lot of things become possible ...  If you look at any of the refactoring books, most of those refactoring actions become much more straightforward, in ways that are fairly deep.</blockquote>

In addition, he illustrated how views can be flexible:

<blockquote>[O]nce it's not text, all of a sudden you can display it in really interesting ways ... You can, for example, turn the square root function into the obvious mathematical notation. You can turn the identifier theta into the Greek letter theta. You can turn division into the horizontal bar with numbers stacked. And we've done experiments with wackier things, such as trying to generate real time flow charts.</blockquote>

Software developers, we need to eat our own dog food. Through the magic of software, we've allowed end-users to view and manipulate databases in countless ways. A single corporate database might be viewed and edited via any number of command-line interfaces, charts, text reports, and web pages. But how about source code? Just a glorified text editor will do, mate.

Eclipse and Idea advance the idea somewhat. They do treat code as structure and are much more powerful on the refactoring side. Also, plugins are available that manipulate this structure to [render code as UML](http://bcs-oops.org.uk/resources/designrecovery/v3_document.htm). But there is so much more to go.

In terms of manipulation, you should be able to manipulate code like a GUI --- altering the source code text of an attribute performs a *rename* refactoring; dragging one class into another makes it an inner class.

In terms of display, data structures could be represented visually (and manipulated that way too). For instance, a multi-dimensional array could be depicted as a filled-in table.  This view would be especially useful during debugging. Lines between words could be shown to indicate relationships. These views don't all have to be on; the point is to make them flexible, in much the same way as systems for experts in other domains. That's the magic of software, and something you can't do with paper: infinite representations of the same data; the right combination chosen based on the user's disposition and situational needs.

As a side note, the idea of representing the code in XML is actually a non-issue. As Jon Udell points out, programmers themselves don't have to touch the underlying structure, and Eclipse/Idea are living proof.