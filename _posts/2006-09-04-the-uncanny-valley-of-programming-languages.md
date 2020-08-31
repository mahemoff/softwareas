---
id: 342
title: The Uncanny Valley of Programming Languages
date: 2006-09-04T15:50:52+00:00
author: admin
layout: post
guid: http://www.softwareas.com/the-uncanny-valley-of-programming-languages
permalink: /the-uncanny-valley-of-programming-languages/
dsq_thread_id:
  - "440665714"
categories:
  - SoftwareDev
tags:
  - Applescript
  - Domain-Specific Languages
  - DSL
  - Programming
  - Programming Language
  - Uncanny Valley
---
Coding Horror mentions <a href="http://www.codinghorror.com/blog/archives/000672.html">Applescript's well-intentioned attempt to feel like English</a>. Quoting <a href="http://daringfireball.net/2005/09/englishlikeness_monster">John Gruber</a>

<blockquote>
<p>The idea was, and I suppose still is, that AppleScriptâ€™s English-like facade frees you from worrying about computer-science-y jargon like classes and objects and properties and commands, and allows you to just say what you mean and have it just work.

<p>But saying what you mean, in English, almost never â€œjust worksâ€ and compiles successfully as AppleScript, and so to be productive you still have to understand all of the ways that AppleScript actually works. But this is difficult, because the language syntax is optimized for English-likeness, rather than being optimized for making it clear just what the f**k is actually going on.

<p>This is why Python and JavaScript, two other scripting language of roughly the same vintage as AppleScript, are not only better languages than AppleScript, but are easier than AppleScript, even though neither is very English-like at all. Python and JavaScriptâ€™s syntaxes are much more abstract than AppleScriptâ€™s, but they are also more obvious. (Python, in particular, celebrates obviousness.) 
</blockquote>

There's a lot to be said for the <a href="http://en.wikipedia.org/wiki/Uncanny_Valley">Uncanny Valley</a> theory: 
<blockquote>
<p>The Uncanny Valley is an unproven hypothesis of robotics concerning the emotional response of humans to robots and other non-human entities. It was introduced by Japanese roboticist Masahiro Mori in 1970. It states that as a robot is made more humanlike in its appearance and motion, the emotional response from a human being to the robot will become increasingly positive and empathic, until a point is reached beyond which the response quickly becomes strongly repulsive. However, as the appearance and motion continue to become less distinguishable from a human being's, the emotional response becomes positive once more and approaches human-human empathy levels.
</blockquote>

<img src="http://img484.imageshack.us/img484/1606/moriuncannyvalleyse4.gif"/>

Just as human emotions (according to that hypothesis) respond in a U-shape curve, so does performance with human-computer interfaces. When we can come up with a near-perfect human language processor, it will probably have some great applications for humankind, allowing "non-programmers" to instruct computers in far more complex ways than they can right now with the most advanced end-user programming interfaces around today (Excel and Second Life).

Until that time, attempts to make programming languages human-friendly, however well-intentioned, fall deeper into the valley. It's like old-school Visual C++ codegen - sounds great at first, but as soon as you get one tricky use case (inevitable), it all falls down.

A more promising approach is Domain-Specific Languages (DSLs), which talk in terms familiar to the "end-user-programmer" (we need a better name for that actor), but, by accepting critical constraints, is actually workable.