---
id: 423
title: Coding Standards Suck
date: 2008-02-13T00:37:44+00:00
author: admin
layout: post
guid: http://softwareas.com/coding-standards-suck
permalink: /coding-standards-suck/
dsq_thread_id:
  - "375573519"
categories:
  - SoftwareDev
tags:
  - Coding Standards
  - Software
---
<tags>Coding Standards, Software</tags>

... because they are dogmatic. Coding <em>guidelines</em> are just fine, but coding standards imply:
<ul>
  <li>There will be an automated tool that checks your conformity to guidelines, leading to (a) inability to check in your code; (b) public shame; (c) much head-banging on keyboards</li>
  <li>A smug sense of unjustified satisfaction from the kinds of people who add little value to the development process</li>
  <li>Developers are thick-heads</li>
</ul>

As a devotee of literate and self-documenting software, I frequently find cases which break my own default preference. A simple example is a data structure where geometrically splendid code layout will aid comprehension, e.g.:
<pre>
  var fibs    = [ 0, 1, 1, 2,  3,  5,  8, 13, 21];
  var squares = [ 0, 1, 4, 9, 25, 36, 49, 64, 81];
</pre>
This is of course laid out so you can easily compare the value at each position in the array. But under some dogmatic coding standards, you are incited to make the code considerably less comprehensible:
<pre>
  var fibs = [0,1,1,2,3,5,8,13,21];
  var squares=[0,1,4,9,25,36,49,64,81]
</pre>
That's a simple data structure example, but the same thing can happen with control flows as well, where you might want to sometimes use whitespace, sometimes use a curly brace at a different place, etc.

Another example - which I've mentioned for years on this blog - is the craziness of setter and getter dogmatism. Instead of:
<pre>
  public void setName(name) { this.name = name; }
  public void getName() { return name; }
  public ...
</pre>

... you end up with:
<pre>
  /* Sets the name. Duh. */
  public void setName(name) {
    this.name = name;
  }

  /* Ehm. Well I suppose it gets the ^$()* name .Bozo!*/
  public void getName() {
    return name;
  }

  public ...
</pre>

... How's that for a five-fold increase in your LOC, if that's what you're getting paid for!

Competent programmers can make these decisions and decide when it's reasonable to deviate from coding guidelines, and if you're relying on an automated system to check code, maybe it's time to start running code reviews or pair programming. The problem is, they're not allowed to by heavy-handed Coding Standards.

In Extreme Programming, coding standards are defended on the basis of collective ownership; the argument is that each team member has their own taste, so code would forever be thrashed back and forth as each programmer rotates on to it. Once again, though, this is fine as long as coding guidelines are in place. The example above is something all programmers can agree on, but would still fail some automated systems, or fail to be generated correctly by a tool like Eclipse. There will still be arguments, but probably not many if the team is thinking alike, and those will be arguments worth having.

There's also a view that coding standards support faster development, by letting you focus more on cranking code out and not on hand-crafting each line of code. Well, I'd rather hand-craft each line of code and make it as valuable as possible, refactoring and refactoring it; IMO a good team and environment can produce code that's one-tenth the size of equivalent code created by a mediocre team. That's ten times less code to maintain and ten times less code to confuse. To wit, 37Signals took TadaList - a reasonably successful app - to production with <a href="http://weblog.rubyonrails.com/2005/01/21/matz-takes-note-of-ta-da-and-rails/">just 579 lines of code</a>. With tight code like that, you ought to treat it more like prose and less like a can of dog food on an assembly line.