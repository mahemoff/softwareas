---
id: 228
title: 'Mocks, Stubs, Dependency Injection, and &#8230; XMLHttpRequest'
date: 2005-10-31T10:09:16+00:00
author: admin
layout: post
guid: http://www.softwareas.com/mocks-stubs-dependency-injection-and-xmlhttprequest
permalink: /mocks-stubs-dependency-injection-and-xmlhttprequest/
dsq_thread_id:
  - "375572702"
  - "375572702"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Dependency Injection
  - Links
  - Mock
  - Mock Objects
  - Software
  - Testing
  - Web
  - Web2.0
  - XMLHttpRequest
---
*"A Mock Is Not So Stupid After All!"*

Dave Crane's been talking about [Mocking the Server-Side](http://dave.sunwheeltech.com/wordpress/2005/10/17/mocking-the-server-side/):

> A Mock Object is a stand-in for the real thing. Few modern programs are really standalone, and enterprise apps require a very complex context in order to operate; containers, databases, directories, web services, etc. This can make testing difficult, because to set up the test and run it, one needs to provide all the necessary context. Mock objects can be thought of as really dumb implementations of a contextual element, one that would never be useful in production, but provides the predictability and ease of setup required for a test. A mock database might always return the same four rows of data, whatever the WHERE clause. A mock web service might always serve up the same XML document.

**So the idea is to create a simulation XML document (or plain-text document) to be retrieved with XMLHttpRequest.**

Dave's followed up with some [good](http://dave.sunwheeltech.com/wordpress/2005/10/30/an-xml-callback-antipattern/) [tips](http://dave.sunwheeltech.com/wordpress/2005/10/30/what-the-file-system-doesnt-tell-you/) to that end. All good timing as I've recently been working on a demo for the final lot of patterns - the process patterns - and one of the refactorings uses a canned plain-text document to illustrate The [Pattern](http://ajaxpatterns.org) Currently Known As "Server-Side Simulation Stubs" (who said alliteration had no place in software writing?).

Worth noting the terminology used, and here I'll be pedantic. Dave refers to a Mock what I call a Simulation Stub. In the past couple of years, **the terms "Mock" and "Stub" have often been used interchangeably, but I think the distinction is worth keeping, because otherwise the [original meaning of Mocks](http://www.mockobjects.com/MocksObjectsPaper.html) is lost**. I don't really care what things are called, but when two concepts become one name, at least one of those concepts is going to get hurt. It's a testament to the creators of Mocks that they managed to produce a name so evocative that it's come to consume a much older concept. ("Stub" and "Shunt" have always been pretty vague terms anyway.)

Under the original definition, **a Mock is an object that verifies how it's being used by a tested object, and by inference, how things like it will be used by the class being tested. Yes, it might spit out simulation data, and it might even have a fancy interface that lets you tell it how to respond. However, those functions are only there to help verify how it's used. It's what goes into the mock that counts, not what the mock pumps out. Corollary: a Mock is <i>not</i> stupid**. It might not win a Nobel Prize anytime soon, but it's smart enough to know what to expect and how to check if that expectation's been met. The mixing of terms has carried over to some parts of the Ruby/Rails community, as [Aslak](http://aslakhellesoy.com/) recently observed during a [RubyConf presentation](http://glu.ttono.us/articles/2005/10/14/top-to-bottom-testing-in-ruby).
 ([Podcast on mocks](http://www.softwareas.com/podcast-mock-objects-and-unit-testing), Fowler's [Mocks Aren't Stubs](http://www.martinfowler.com/articles/mocksArentStubs.html).)

In a web context, what might the distinction mean?

* **A Simulation Web Service** (or a "Stub Web Service", but I prefer "Simulation") is typically some XML or plain-text document that's been written manually. It could also be a bit more sophisticated, offering a means for the server-side developer to tweak its output.
* **A Mock Web Service** is a server-side script that's been configured to expect a certain sequence of XMLHttpRequest messages, and will carp as soon as the sequence is broken.

As Dave's articles explain, a Stub Web Service is certainly a useful thing, and I suspect quite a few developers follow that practice. (Please tell me about it if you do!)So how about Mock Web Services? That's pure speculation!! I could see the benefit, but I've not done it, haven't heard of anyone doing it, and I seriously doubt there are any frameworks that facilitate it.

**A variation on Simulations and Mocks would be a completely browser-side approach, in which you adopt an XMLHttpRequest wrapper, and make it output a dummy document while in "testing" mode.** This raises further questions:

* **How are mocks handled in Javascript?** Well, William Taysom recently noted that you can [approximate method_missing](http://www.jadetower.org/muses/archives/000388.html), and a Mock library like the awesomely useful [JMock library](http://jmock.org) is clearly feasible. **There are a few JUnit equivalents out there, so why not a mock lib?** (Would you use such a thing?) If you say that would be over-engineering, then the same  charge could be made about JS testing in general, since mocks are really a natural consequence of unit testing and TDD ... any time you find yourself testing an event mechanism, a mock might be a good idea.
* **How to switch context in Javascript?** Okay, so mocks are a big reason for the rise of Dependency Injection and "lightweight" ([as if the implementation matters](http://www.almaer.com/blog/archives/000846.html)) containers in Java/J2EE/JEEWhiz. Well then, doesn't Javascript need the same thing? Again, I know, "you're over-engineering it, Mahemoff".  So maybe I am. **It's been said that [Dependency Injection doesn't do much for Ruby](http://www.onestepback.org/articles/depinj/index.html), and maybe the same's true for JS. So how then, do you make your browser app switch between a mock web service and a production service? The answer is not, "change the source code", because to achieve continuous integration, you want to keep an automated test around that calls the mock service. Maybe the best thing to do is rely on DI - or some other context-switch mechanism - in the server, so that the Javascript that it spits out will differ according to the environment.**