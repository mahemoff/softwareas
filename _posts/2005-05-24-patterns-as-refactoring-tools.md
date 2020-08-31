---
id: 135
title: Patterns as Refactoring Tools
date: 2005-05-24T23:03:17+00:00
author: admin
layout: post
guid: http://www.softwareas.com/patterns-as-refactoring-tools
permalink: /patterns-as-refactoring-tools/
dsq_thread_id:
  - "376807934"
  - "376807934"
categories:
  - SoftwareDev
---
Fowler's original [refactoring text](http://www.refactoring.com/) was based on a number of patterns. So you have a refactoring like "Introduce Null Object" which is a direct mapping to the older ["Null Object" pattern](http://c2.com/cgi/wiki?NullObject).  Now there's also Joshua Kerievesky's ["Refactoring to Patterns" book](http://www.industriallogic.com/xp/refactoring/catalog.html) which makes the idea more explicit. And in a new interview with bill Venners, Erich Gamma makes [similar comments](http://www.artima.com/lejava/articles/gammadp3.html). There are two themes here: **pattern refactoring for education**, and **pattern refactoring for development work**.

## Pattern Refactoring for Education

Gamma on teaching patterns (emphasis mine):
> I think what you should *not* do is have a class and just enumerate the 23 patterns. This approach just doesn't bring anything. You have to feel the pain of a design which has some problem. **I guess you only appreciate a pattern once you have felt this design pain.**

Venners on the JUnit discussion (emphasis mine):
> you walk the reader through the design of JUnit by, as you wrote, "starting with nothing and applying patterns, one after another, until you have the architecture of the system."

I remember coming across the JUnit cookbook a few years ago. It was the first design I've seen described as a series of refactorings, and it struck me just how clear the whole thing was. I've only had an opportunity to use the technique once, and it certainly worked better than the usual walkthrough.

The interview also points out that patterns in general are an excellent way to learn about OO principles like polymorphism and the other usual suspects. As I've written here before, principles and patterns go hand-in-hand. A well-considered set of patterns shows how to produce designs that adhere to a particular set of principles. We've traditionally taught principles and used examples to illustrate. That's too much distance. **Patterns are the missing link between principles and examples**.

## Pattern Refactoring for Education

Gamma on practical application of patterns:
> Do not start immediately throwing patterns into a design, but use them as you go and understand more of the problem. Because of this **I really like to use patterns after the fact, refactoring to patterns**.

Again, I think this has been a surprising aspect of patterns. It follows from the popularity of refactoring and TDD and feature-driven design. Didn't Kent Beck say something like "Get it working, then get it right". With much less big upfront design, it only makes sense that patterns are used on a pull basis.