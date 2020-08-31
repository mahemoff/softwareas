---
id: 1438
title: 'Jeremy Ashkenas: CoffeeScript [Full Frontal 2011 Live Blog]'
date: 2011-11-11T10:33:47+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1438
permalink: /jeremy-ashkenas-coffeescript-full-frontal-2011-live-blog/
dsq_thread_id:
  - "468323157"
categories:
  - SoftwareDev
tags:
  - CoffeeScript
  - Conference
  - Javascript
---
Live blogging at [Full Frontal 2011](http://2011.full-frontal.org/), where 
Jeremy Ashkenas is first up, presenting on CoffeScript.

![](http://s1-03.twitpicproxy.com/photos/large/445113979.jpg)

### Motivation

Good work is being done inside and outside of the TC39 committee. The next
version of JavaScript is an open process, a working mailing list you can get
involved with, and there's a chance to experiment and shape it.

"It's just JavaScript": CoffeeScript is not about creating a new language or
letting us apply an existing language in a browser.

### Bootstrapping

Original version of CoffeeScript was written in Ruby, but as v0.5, it became 
significant enough to bootstrap it: Ruby builds an initial CoffeeScript
compiler, which then compiles the real CoffeeScript compiler. Slightly more
complicated, but you get the idea: CoffeeScript is basically written in 
CoffeeScript.

### Language Features

* No "var"
* No "function"
* Significant whitespace
* Comprehensions:
[code]
  for stooge in list
    console.log 'hi ' + stooge
[/code]

* Block strings and interpolation  (works for regex's too):
[code]
"""
An old pond
a #{animal} jumps in
the sound of water
"""
[/code]
<ul>
<li> Object-oriented, and unlike normal prototype stuff, you get to call super.
<li> Binding "this" to the actual object with =&gt;
</ul>

### How it happens

Instead of waiting for a standards body or a browser to give you the language, 
you can roll your own today. CoffeeScript uses Jison for parsing, there's also 
Pegs if you prefer. A nice tip is "it's okay to cheat"! CoffeeScript uses a 
strict tokeniser to disambiguate, making the parsing much easier than if it 
allowed all sorts of ambiguities.