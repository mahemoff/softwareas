---
id: 392
title: 'The only thing wrong with GoF Design Patterns is &#8230;'
date: 2007-07-26T00:31:56+00:00
author: admin
layout: post
guid: http://www.softwareas.com/the-only-thing-wrong-with-gof-design-patterns-is
permalink: /the-only-thing-wrong-with-gof-design-patterns-is/
dsq_thread_id:
  - "375573341"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DesignPatterns
  - Gamma
  - GoF
  - Links
  - Patterns
  - Software
---
Jeff Attwood recently pointed out <a href="http://www.codinghorror.com/blog/archives/000899.html">the difference between Gamma et al's Design Patterns and Alexanders' equivalent</a> and outlined a critique of the former which characterises it as "replacing actual thought and insight with a plodding, mindless, cut-and-paste code generation template mentality".

First, I want to note that the critique above surely defies belief to anyone who has used the patterns in practice. Patterns like the GoF design patterns are grammar for software architecture. If you search the technorati archives from when grammar emerged many millennia ago, you will probably find one or two bloggers was bemoaning the loss of creativity that this concept of sentence structure will cause. Fortunately, sense prevailed and now writers can be creative about the things that matter and not have to micromanage those that don't. The progression of any discipline involves a cycle experimentation followed by optimisation followed by explicit statements of best practice (patterns), spiralling upward in level of abstraction.  If I was so inclined, I'd go make a T-Shirt on CafePress that says "Patterns Take You Higher" with a picture of Bob Marley refactoring to Template Method.

So <a href="http://www.amazon.com/exec/obidos/tg/detail/-/0201633612?v=glance">the GoF patterns</a> are perfectly choice by me. The main problem with them is not the content per se, but the fact that <strong>most software developers think that pattern==GoF pattern and pattern language==the 23 patterns by Gamma et al. (1995).</strong>. If there's ever a sequel, it would double the number of patterns in the universe according to these folks! In fact, there are thousands and thousands of documented design patterns out there, in the realm of software alone. (Admittedly, the most popular realm for design patterns, though there are still plenty of patterns for other disciplines too.)

This perception is silly.

Why do software patterns != GoF patterns? We can expand out from the GoF patterns in several dimensions (even staying within the realm of software):
<ul>
  <li><strong>Architectural Paradigm</strong> Even with patterns of high-level software structure, like GoF, we can model different architectural paradigms. GoF is all about general-purpose OO architecture; if you wanted to work with functional or logical languages such as Haskall or Prolog, you would need different kinds of patterns.</li>
  <li><strong>Application Type</strong> GoF patterns apply to the general structure of any medium+ scale architecture. There is still a wealth of advice to be gained from studying existing applications of the same type as you're working on. This could be web server design, in-browser script design (like some of the Ajax patterns), mobile phone design, etc. For instance, the various J2EE patterns around, which were probably the second best known category of patterns in the industry (trailing GoF by a long margin though).</li>
  <li><strong>Perspective</strong> People see software from different perspectives; GoF patterns see it from that of a technical architect working close to the ground. You can also see patterns from the perspective of a user experience designer (usability patterns), project manager (software development process patterns), business analyst (business process patterns), programmer (coding idioms), etc.  In <a href="http://mahemoff.com/paper/candidate/">this paper</a>, we explained how patterns for usability alone could have all sorts of representations.</li>
  <li><strong>Domain</strong> The GoF patterns apply whether you're working in banking, gaming, or web design. But each of those fields have their own idiosyncracies and fortunately there are pattern languages which capture them.
  <li><strong>Opinion</strong> Even if you aim for the same problem space as Gamma and colleagues looked at, you will have your own views on the correct solutions. <a href="http://mahemoff.com/paper/language/">Patterns are opinionated</a>, not objective, so your patterns will differ from theirs. As time goes on, any static set of patterns will naturally become less valid - it's a testimony to Gamma et al that the patterns remain so very useful 12 years on (that's a 256-fold increase in processing power according to Moore's Law, and industry transition from C++ through Java and .Net through to Javascript, Ruby, and Python). Still, they're not perfect; <a href="http://blogs.msdn.com/scottdensmore/archive/2004/05/25/140827.aspx">Singleton anyone?</a>
</ul>

One of the reasons the Gamma patterns are so successful is the fact that they apply so universally. However, this also leaves room for other patterns to come in and provide more specialised support.

Ajax Patterns has certainly been subject to this misconception; one review liked the content but prefers not to see it as a real pattern book - "Anybody who has read a real design pattern book and then read this book will soon feel the artificiality. " Another refers to Gamma et al as "I read the original 'Design Patterns' book" and states "Those that read the original book will understand that packaging these topics as design patterns is insulting to those that know the value of actual design patterns. ". After many years of explaining usability patterns, I had anticipated these concerns with an appendix explaining the difference, but moreover explaining that it's the content that matters most. There is also a perception that "Patterns" in the title sells more copies; all I can say is "I wish" as that buzzword went out the window around 2002. It's called "Ajax Design Patterns" because they are, well, Ajax Design Patterns.

Bill Sanders gets it and <a href="http://www.as3dp.com/2007/06/19/more-than-one-design-pattern-set/">recently discussed this phenomenon</a>:

<blockquote>
<p>Buried in Appendix C (pg 605), Mahemoff distinguishes his use of design patterns from that of GoF, but it is not the kind of place that most developers are going to look when they pick up a book about Design Patterns. Likewise, Mahemoff uses the inside front and back covers to list the Ajax design patterns. On the one hand, anyone who reads those pattern names is going to know that this book is not about the kinds of design patterns GoF examine. On the other hand, the fact that the patterns are listed there, just like the GoF book, is a sincere form of flattery in the form of imitation.</p>
</blockquote>

Bill makes a good point about the Appendix C content being buried. Actually, relating the second point back to the first, I had in mind the similar statement by Gamma et al about Alexander's patterns and their relevance, which also appears at the end. Still, in a pattern book, I'm not sure where to put something meta that won't be buried; I'm sure the preface and intro are read about as much as the appendices. And I've certainly discussed the issue online before.

As for the covers, I liked the idea from GoF as well as Fowler's UML Distilled book, and was particularly insistent on this because O'Reilly couldn't do page cross-referencing.

<blockquote><p>
Mahemoff is quite right in noting that the â€œoriginalâ€ design pattern book is Christopher Alexander et alâ€™s town planning and architecture patterns book from the 1970s.(In fact in the Foreword to GoFâ€™s DP book, Grady Booch mentions Christopher Alexanderâ€™s work.) However, <strong>common usage of design patterns in the context of computer programming has come to mean the kinds of patterns GoF talks about</strong>. Head First Design Patterns is a good example. No one was disappointed because they were surprised by the meaning of design patterns. Common usages in a given context come to have a specific meaning. In the world of quilt-making, design patterns mean something entirely different than in programming, and so no one is surprised when they get a book called Quilt Design Patterns and find out that thereâ€™s nothing about the Creational, Structural, Behavioral Design Patterns. However, in the world of programming, that is exactly what can (and did) happen in the case of Ajax Design Patterns, despite the fact that no less than Ralph Johnson reviewed parts of it.
</p></blockquote>

(Emphasis mine) Yep, if you published a book of music patterns, there'd be no confusion. Still, I think our industry misses out because of this confusion. In an ideal world, there would have been 2 or 3 equally big hits at the same time, to get people's mind around the fact that patterns are everywhere, not confined to the one (albeit excellent) text (I was going to call it "bible" but the one time I met John Vlissides, he told me he didn't like it when his colleagues called it that :)). As it is, there's the big 'un, a few prominent others - typically in similar "high-level architecture" style to that one (e.g. the J2EE books, <a href="http://www.cs.wustl.edu/~schmidt/POSA/">the POSA series</a> and some of Fowler's work), a bunch of books which used "pattern" for the hype value, and thousands of other books and one-time papers and blog entries. At one stage, Ward Cunningham was going to work with Microsoft to build <a href="http://en.wikipedia.org/wiki/PatternShare">PatternShare</a>, a kind of meta-repo for all things pattern, which may have changed things, but apparently it never happened and the site is now down.

<blockquote>
Quite apart from the bookâ€™s title, Mahemoff, does take up the invitation to contribute to design patterns offered up by GoF and he documents a number found in Ajax. While on a different level and with a different specific meaning than that found in GoF book, Mahemoff provides a wider view of design patterns and has what may be the best Ajax book on the market. It would be a shame if his work is diminished by the title, but among some, especially on the higher end, that may happen. Fortunately, the bulk of the reviews are readers who were looking for a good Ajax book and got exactly what they wanted.
</blockquote>

This is where things get even more confusing, because the Ajax patterns (as with just about any other form of software pattern) actually relate to he GoF patterns. They're different, but not entirely orthogonal. For instance, the daddy of all UI patterns, Observer, is present in patterns such as <a href="http://ajaxpatterns.org/Virtual_Workspace">Virtual Workspace</a>. My attitude is that patterns are there to be referenced and so I will happily reference other patterns from other languages if need be. In my mind, it's all one big network of patterns (a PatternShare wiki, if you will).