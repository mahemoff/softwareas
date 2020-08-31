---
id: 192
title: Reading Open-Source Code
date: 2005-09-08T15:38:41+00:00
author: admin
layout: post
guid: http://www.softwareas.com/reading-open-source-code
permalink: /reading-open-source-code/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572521"
  - "375572521"
categories:
  - Links
  - SoftwareDev
tags:
  - Design
  - Java
  - JavaEE
  - Javascript
  - Links
  - Object-Oriented
  - Scriptaculous
  - Software
---
Dave Crane [looks into](http://dave.sunwheeltech.com/wordpress/2005/09/07/the-coders-pyramid/) some [Scriptaculous code](http://script.aculo.us). The main point is that Scriptaculous is easy for novice JS programmers to use, but the source code would be difficult, for novices at least, to understand. Which raises these questions:

> So, going back to the bigger picture, hereâ€™s something for the authors of JavaScript libraries to consider. How much of a gap are you creating between using your library, and being able to modify or enhance it? Does such a gap present a barrier to its uptake? Should good code be there to be read as well as executed? 

**In theory, the implementation of a library shouldn't matter to developers using it. That's because a good library should offer components that are open for extension, but closed for modification - the [open-closed principle](http://davidhayden.com/blog/dave/archive/2005/06/04/1096.aspx). Thus, you should be able to treat the library as a black-box and only care about the API it presents - you never have to maintain it, so why read the code?**

But it's usually not so simple. You might not need to change the code, but you do need to understand it. In an ideal world, there would be abundant documentation. But agile says that all that documentation is valuable, but self-documenting code is much more valuable. In similar vein, **the availability of code is often justified as a reason for open-source projects to include less documentation (among other benefits). So open-source code had better be understandable, ideally <a href="http://mahemoff.com/paper/software/SelfDocumentingSPA2005/selfdocumentingSpa2005.html">self-documenting</a>, but at least well-commented.**

I have used (by "used", I mean "wrestled against in a cage match") a couple of very prominent Java EE frameworks where implementation code is confusing and badly in need of refactoring, with most of the code comments in "TODO" and "Weren't you going to fix this?" territory. I was stuck and documentation was insufficient, so I could only turn to the source code for help. And that's actually a pretty good place to work out what's going on anyway. But, alas, the code did not come to my aid. ** Perhaps that's the natural consequence of an open-source project becoming a startup with a support-based revenue model, but it makes a mockery of the code-as-documentation argument for open-source.**

The Scriptaculous implementation is good for anyone who knows Javascript, which is all you could hope for ... just because it's API is simple enough for novices, doesn't mean its implementation has to be. In fact, the implementations of "Puff", "Fade", and so on, are actually extensions of the base functionality, and any developer could create their own effects in the same way. The Effect framework is **an example of how Javascript can provide decent support for Domain-Specific Languages, in Scriptaculous's case, a grammar of visual effects**. Also, if only want to use an existing effect, but with a little variation, some of them accept an options specification.