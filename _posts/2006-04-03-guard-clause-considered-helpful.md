---
id: 289
title: Guard Clause Considered Helpful
date: 2006-04-03T09:50:22+00:00
author: admin
layout: post
guid: http://www.softwareas.com/guard-clause-considered-helpful
permalink: /guard-clause-considered-helpful/
dsq_thread_id:
  - "375438739"
categories:
  - SoftwareDev
tags:
  - Programming
  - Self-Documenting
  - Software
---
Apparently, PragDave recently questioned the conventional wisdom about <em>GOTO considered harmful</em> (does this mean all <a href="http://www.google.co.uk/search?q=%22considered+harmful%22">"X considered harmful"</a> articles will be retrospectively struck off the record?). <a href="http://ivan.truemesh.com/archives/000611.html">Ivan Moore's</a> given an example as to why the rule of "a single exit point" sucks, and I agree.

<strong>Another reason for multiple exit points is <a href="http://www.refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html">guard clauses</a></strong>. Code units, like classes or functions, ought to look right at a high level. Just like with a piece of writing, it's important that the overall structure gives you the big picture. Guard clauses help here. <strong>You can say, "Okay, let's get the cruft out of the way - the trivial cases, the exception cases - and now we can focus on the main thing the function's meant to do."</strong>


[java]
void foo() {
  if (nothingToDo) { return; }
  // Implement typical behaviour of foo()
}
[/java]

is much more readable than:

[java]
void foo() {
  if (!nothingToDo()) { // Hold my breath until the end
    // *ugh* The typical behaviour buried in an if-clause
    // And adding insult, we're now indenting more than we need to
}
[/java]

<a href="http://stevef.truemesh.com/archives/000612.html">Steve Freeman points out</a>, Ivan's particular example could be refactored nicely into a single ternary operator statement. While they don't scale to larger, more complex, functions, ternary operators are a very handy tool for the reason he explains.