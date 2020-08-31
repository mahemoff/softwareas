---
id: 62
title: String, CharSequence, and the curious naming of length()
date: 2005-02-22T00:35:49+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=62
permalink: /string-charsequence-and-the-curious-naming-of-length/
categories:
  - SoftwareDev
---
[Simon Harris](http://www.almaer.com/blog/archives/000730.html) (chapeau [Dion](http://www.almaer.com/blog/archives/000730.html)) discusses CharSequence, the interface String and StringBuffer decided to conform to since J2SE 1.4. CharSequence gives you an okay interface with which to enjoy the goodness of mock onjects and the like. However, it's nothing to rave about as it lacks most of the methods in String, and as Simon points out, it's mutable where String is not. A MutableCharSequence sub-interface would be a nice contribution.

In any event, CharSequence is unfortunately not a lot of use for one simple reason: it is largely unknown. APIs almost exclusively rely on String rather than CharSequence, so you'd have to continually "(String) seq" downcast or "toString()" convert to interact with any libraries, including the Java API.

While we're on the topic of *String*, how about a "getLength()" method aliased to the unfortunately named "length()"? It wouldn't be a true Javabean property due to the lack of a "setLength()" method, but good enough for most bean-based frameworks to read it as a property. In particular, JSPs would be easier if you could do a getProperty or a $s.length in JSTL. (And I could say similar things about Collection.size().)