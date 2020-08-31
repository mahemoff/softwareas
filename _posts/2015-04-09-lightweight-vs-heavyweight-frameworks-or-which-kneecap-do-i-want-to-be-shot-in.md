---
id: 2108
title: 'Lightweight vs heavyweight frameworks. Or, &#8220;which kneecap do I want to be shot in&#8221;'
date: 2015-04-09T20:11:52+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2108
permalink: /lightweight-vs-heavyweight-frameworks-or-which-kneecap-do-i-want-to-be-shot-in/
categories:
  - Uncategorized
---
Very sensible commentary on software frameworks and the dichotomous debates that afflict them.

"""
Using a lightweight, comprehensible framework is good, until you hit the limits of that framework and start pulling in lots more libraries to fill the gaps (the Sinatra/Cuba world). Using a heavyweight, complete library is good, until you start suffering from bugs caused by incomprehensible magic buried deep inside (the Rails world).

...

<strong>The underlying problem isn't fashion, or bloat. It's that software is very, very complex.</strong> Unless you're doing hardcore embedded work in assembly language, you're building a raft on an ocean of code you won't read and can't understand.

A friend of mine put it well once. He said that you should have deep understanding of systems one layer from yours (ie your frameworks), and at least a shallow understanding of things two or three layers away (operating systems, etc).
"""

The last comment is similar to what I learned from the wisdom of Spolsky: Take control of one level below your primary level of abstraction.

<a href="https://news.ycombinator.com/item?id=9347318">https://news.ycombinator.com/item?id=9347318</a>