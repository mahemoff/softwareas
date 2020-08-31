---
id: 398
title: Operator Overloading Considered Insanely Useful
date: 2007-08-03T23:54:55+00:00
author: admin
layout: post
guid: http://www.softwareas.com/operator-overloading-considered-insanely-useful
permalink: /operator-overloading-considered-insanely-useful/
dsq_thread_id:
  - "375573386"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Programming
  - SelfDocumenting
  - Sugar
  - Syntax
---
I am amazed that for all the talk about future Java features, there is hardly any mention of operator overloading. Certainly syntactic sugar is high on the priority list, with the Java world starting to realise the benefits of powerful literals and closures. (Good thing too. <a href="http://steve-yegge.blogspot.com/2006/09/bloggers-block-4-ruby-and-java-and.html">Steve Yegge:</a> "Java's biggest failing, I've decided, is its lack of syntax for literal data objects. It's an umbrella failing that accounts for most of the issues I have with the language."). Yet operator overloading is another feature that no real-world language should be without, and hardly anyone gives a second thought to the fact that time has moved on since the concept was rejected in 1995.

In Java:

earnings2007.greaterThan(earnings2008)

In Ruby/Python/C++/C#/anyOtherDynamicOrNonDynamicLanguage:

earnings2007 > earnings2008

Of course, many a Java destractor has noted the irony that is String."+" overloading, which is to say that Java's creators broke the rule and did something you can't do, by making "a"+"b" a legal operation, even though String in theory is just a run-of-the-mill Java class. This is a subtle way of saying maybe there are cases where operator overloading makes sense; at least, the people who prohibited it thought so. I think it's called "do as I say...".

The arguments against operator overloading are pretty much the same as those against dynamic classing and make a trade-off in favour of robustness over productivity which is rarely warranted. The reality is that production errors are hardly ever caused by typing confusion, as long as you make the operator definitions meaningful. I can trust you to do that because you're a professional, right? Even if your testing regime consists of nothing more than dipping your web server into your bowl of Corn Flakes every weekend, I challenge you to come up with a production error caused by confusing String.+() with Integer.+(). If you can grok earnings2007.greaterThan(earnings2008), I'm sure you'll do just fine with earnings2007 > earning2008. The only problem with operator overloading comes when people do stoopid things with operators, and you can just as equally do stoopid things with method names (or <a href="http://en.wikipedia.org/wiki/FALSE">booleans</a> if you want to get really sad :)), so why victimise the operator?

People will say "can't have operator overloading - it leads to weird code that doesn't make sense", which would be like banning electric guitars because someone might use it to make weird music.

I would take overloading further than what we do today. e.g. how about multiple operands:

assert(x < y < z)

You could do that with today's terminology by having < return some kind of state object instead of just a boolean. So what I'm talking here is as much about patterns as new language features.

How about more <a href="http://www.zipcon.net/~swhite/docs/math/math.html">visual representations</a>:

<div class="math">
	<span class="int">&int;<sub>&Omega;</sub><sup>&nbsp;</sup></span>
		<i>v</i> &Delta; <i>u</i> <i>dx</i>

	&nbsp;=&nbsp;
	<span class="int">&int;<sub>&Omega;</sub><sup>&nbsp;</sup></span>
	<span class="sum">&sum;<sup>&nbsp;</sup><sub><i>i</i></sub></span>
		<i>v</i><sub><i>x</i><sub><i>i</i></sub></sub> 
		<i>u</i><sub><i>x</i><sub><i>i</i></sub></sub> 
		<i>dx</i>

	&nbsp;+&nbsp;
	<span class="int">&int;<sub>&part;&Omega;</sub><sup>&nbsp;</sup></span>
		<i>v</i> 
		<table class="fraction" cellpadding="0" cellspacing="0">
		<tr><td class="numerator">
			<i>d</i><i>u</i>
		</td></tr>

		<tr><td class="divider">----</td></tr>
		<tr><td class="denominator">
			<i>d</i><i>n</i></td></tr>
		</table>
		&nbsp;<i>d</i><i>S</i>
</div>

Yes, that's right, a formula that looks like a formula. Surely this is the natural extrapolation from current trends - (a) domain-specific languages, where the code looks like the requirement; (b) smart IDEs. I discussed this <a href="http://softwareas.com/source-code-string-of-ascii-or-tree-of-goodness">a while back</a> with reference to the (now-defunct?) Jackpot project. Operator overloading is one piece of that puzzle.

<img src="http://picupper.com/2007/08/03/cookiej.jpg" />