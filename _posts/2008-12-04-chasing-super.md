---
id: 498
title: Chasing super
date: 2008-12-04T02:35:13+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=495
permalink: /chasing-super/
dsq_thread_id:
  - "375574006"
categories:
  - SoftwareDev
tags:
  - Ajax
  - AjaxPatterns
  - Javascript
  - Object-Oriented
  - OO
  - super
---
<img style="width: 380px;" src="http://i84.photobucket.com/albums/k14/onemanP/superman.jpg"/>

A lot of discussion around object-oriented Javascript involves finding cunning methods to get a super reference. This is sometimes a reference to the super class, the super instance, or the super version of the current method. <a href="http://ajaxian.com/archives/super-js">The latest installment in an Ajaxian posting this week on work by Erik Arvidsson</a>. It makes for an interesting enough intellectual exercise and I have full respect for anyone who can pull these things off. But as Erik himself <a href="http://erik.eae.net/archives/2008/11/27/12.54.49/">has</a> <a href="http://erik.eae.net/archives/2008/11/14/23.47.04/">commented</a>, is it really worth it? ("Once again I find that adding code to make things simpler in JS is unsuccessful. The costs for adding better ways to do things donâ€™t pay for itself. (Except for the inherits function of course.")

In the case of super...how useful is super - any of the types of super - in practice? In a more general sense, it seems that most discussions of OO and inheritance in Javascript focus more on mimicking the features of typical OO languages and less about how they are actually used. We're thinking more about the design patterns of implementation - how to "do OO" - than the much more important design patterns of application.

super isn't very useful for two reasons:

<ul>
	<li><strong>Inheritance is overrated.</strong>
<p>Inheritance is often considered the killer app of OO. In fact, the killer app is encapsulation - combining data and behaviour in a single model. Inheritance is a great feature, but it's icing on the cake compared to the magnificence of encapsulation. Also, as <a href="http://en.wikipedia.org/wiki/Design_Patterns ">the uber-uber GoF patterns book</a> emphasised, delegation often trumps inheritance. In enterprise Java-land, this has now been firmly entrenched by the dependency injection "revolution". The idea is basically small dumb things, loosely connected, just like the Unix philosophy and that of Web 2.0. You have a small Strategy class that does just that, and you can inject it into many and varied classes. You just wire up the dependencies, outside of both classes. What you don't have is a whopping big monolithic class with loads of subclasses that each have their own subclasses doing different things. The delegation model relies on contract inheritance, i.e. Interfaces in Java terms, but not on behaviour inheritance. Inheritance is often confused for design-by-contract, especially in languages like C++ which don't have an explicit Interface construct.</p>
<p>The popularity of tools supporting delegation and dependency injection, Spring in particular, means many developers are learning this principle by sheer osmosis if not explicitly. Likewise, the <a href="http://en.wikipedia.org/wiki/Duck_typing">duck typing</a> of languages like Ruby and Python - and, notably for our purposes, Javascript - means you can do this stuff well without any special frameworks. Furthermore, even with Ajax starting to reach some level of maturity, most Ajax apps are orders of magnitude smaller than those enterprise apps whose complexity is a key motivation for inheritance. Inheritance? Good, very good...but overrated.</p></li>
	<li><strong>super is a code smell.</strong> <p>For those occasions when inheritance is appropriate, super still remains inappropriate in most cases. If you take a gander at the aforementioned GoF patterns, you'll see that most inheritance-related patterns rely on the superclass calling particular methods on the subclass (usually protected methods). These are methods the superclass has explicitly defined and knows about. As long as the protected method fulfills its contract correctly, everything works nicely. There's no need to call super.</p></li>
</ul>

The more fundamental point here? Javascript ain't Java! Every language is unique.