---
id: 55
title: Java The Dynamic
date: 2005-02-12T12:25:30+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=53
permalink: /java-the-dynamic/
dsq_thread_id:
  - "375572167"
  - "375572167"
categories:
  - SoftwareDev
---
Java can be dynamic too. Somewhat, anyway. **Some blogs have recently looked at static versus dynamic mindsets, and it's all part of a mindset dichotomy throughout the industry.**

Bruce Eckel recently noted that [Java is evolving towards semi-static, semi-dynamic](http://onthethought.blogspot.com/2005/02/more-powerful-than-c-too.html) :
<blockquote>
Java attempts to straddle the gap between statically-typed languages like C++ and dynamic languages like Python, Smalltalk, Ruby, etc. In fact, I think that Java's biggest contribution may be as a bridge to dynamic languages, just like C++'s contribution was a bridge from procedural to OO.
</blockquote>

While most of Bruce's argument is based on the new features of J2SE5, it could also be based on older features too. Reflection, dynamic proxies, and byte-code manipulation have paved the way for dynamicish frameworks like [JMock](http://www.jmock.org) and the various AOP offerings.

A few days later, Bill Venners wrote something rather complementary to that post. In "Static Versus Dynamic Attitude", he outlines a design dilemma: essentially, how to represent a bunch of attributes ... as a Javabean or as a Map. This is a problem which often arises in multi-tiered architectures, because it is usually necessary to pass a cluster of data between layers. For instance, passing a Value Object from an EJB to a Struts action, or passing a result set from a Data Access Object to an EJB.

Well, the answer firmly depends on your mindset. **If you're statically inclined, there's no two ways about it: the Javabean will give you the benefits of type-checking and name-checking. If you're dynamic, you'll fall for the Map every time: why waste time adding behaviour-less POJOs that clutter to the code base, when realistically, you'll probably get the name and type right anyway.** Even if you do err, you'll find any runtime errors soon enough anyway. The  usual Java way would be static, but the point of this article is to question that logic: ** why should the dynamic arguments apply to a Python program, but cease to apply to a Java program?**

**At one level, this is the [Sapir-Whorf Hypothesis](http://www.angelfire.com/journal/worldtour99/sapirwhorf.html) applied to Java.** The Sapir-Whorf Hypothesis says that people think according to the language(s) they speak.  It's certainly relevant to programming languages --- there's even a [Wikipedia entry on that topic](http://en.wikipedia.org/wiki/Sapir-Whorf_and_programming_languages).

**However, it's more than just language. It's culture. Mainstream software development has two threads running through it.** One group takes a risk-averse view and likes well-defined contracts, checking with compilation and grammars. The other group is willing to add a degree of risk to cut this overhead. It's Hani's [Good Versus Evil](http://jroller.org/page/fate/20040923). It's [Adam Bosworth's](http://www.adambosworth.net/archives/000031.html) "two diametrically opposed tendencies":

<blockquote>On the one hand we have RSS 2.0 or Atom ... On the other hand we have the world of SOAP and WSDL and XML SCHEMA and WS_ROUTING and WS_POLICY and WS_SECURITY and WS_EVENTING and WS_ADDRESSING and WS_RELIABLEMESSAGING and attempts to formalize rich conversation models ... On the one hand we have Blogs and Photo Albums and Event Schedules and Favorites and Ratings and News Feeds. On the other we have CRM and ERP and BPO and all sorts of enterprise oriented 3 letter acronyms.</blockquote>

So should you use a dynamic solution in an environment where the mindset is static. Of course, if it's the best solution. **It comes down to pragmatism, and that's not a cop-out, because the only way to make a pragmatic decision is to make the effort to inform oneself of  all the options.** As [Bruce Eckel's followup post](http://onthethought.blogspot.com/2005/02/static-versus-dynamic-attitude.html) points out, "if I learn a new language that has a different way of thinking, then I can go back to a previous language and apply that way of thinking".