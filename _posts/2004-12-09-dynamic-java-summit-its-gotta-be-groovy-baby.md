---
id: 16
title: 'Dynamic Java Summit: it&#8217;s gotta be Groovy Baby'
date: 2004-12-09T19:16:15+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=13
permalink: /dynamic-java-summit-its-gotta-be-groovy-baby/
categories:
  - SoftwareDev
---
Dynamic Java can't come fast enough. So it's good to see a [Dynamic Java summit](http://http://www.tbray.org/ongoing/When/200x/2004/12/08/DynamicJava) (via [The Server Side](http://www.theserverside.com/news/thread.tss?thread_id=30462) was held by Sun,. It brought together several dynamic language heavyweights, including leads of Python (Guido), Perl (Wall), and Groovy ([Strachan](http://radio.weblogs.com/0112098/)). A moment reminiscent of a certain [April Fool's Day announcement](http://use.perl.org/article.pl?sid=01/03/31/206248).

Dynamic Java can't come fast enough. I firmly believe the future is [Groovy](http://groovy.codehaus.org), because it is designed to be as close to Java as possible. Any dynamic language language is intrinsically different. But why make it any more different than it needs to be? With a hybrid like [Jython](http://www.jython.org), you have to use subtly ** different syntax** for everything. Do I "add" to a list or "append" to it? How about when I concatenate strings? Even worse, you have **different semantics** too. If I add an element to a list, will it go the end or the beginning?

It's even possible to have a Jython list and Java list in scope at the same time. Total confusion!

(I'm not bagging Jython in particular - it's served it's purpose well and just happens to be the most successful of the hybrid-style approaches.)

A Groovy list is basically a Java list. It might add some convenience methods and give you some nice script-like syntax, but you'll still add with add() and you'll know all that will come from it. Multiply that effect by thousands of classes, and you start to glimpse the power of a dynamic language building on something you already know. Because it's developed with Java in mind, Groovy libraries will likely focus on wrapping Java libraries, and will evolve much faster. Tricky corner cases will be rare.

Now you could argue it's a waste to develop a whole language around another language.  You could say Java's good and Python's good, so we should just create a little binding between the two, i.e.  by writing bytecode from Python. And we could have a Java-Ruby binding and so on. And a Python-Ruby or a Python-C# too if we like. This many-to-many mapping might seem more efficient, because all of the languages can develop independently and you end up with more choices. In contrast, Groovy will only really work with Java, so any Groovy work is wasted when it comes to creating a dynamic language for C# or C++.  It's a one-trick pony.

I don't buy that argument. Two independent languages cannot easily be combined together, for the reasons described above. They will always have different idioms, different developer populations, different syntax, different semantics. For a language as popular as Java, it makes sense to create a dedicated dynamic language. And I, for one, am looking forward to scripting where it makes sense to do so. Including build management, UIs, and business rules.