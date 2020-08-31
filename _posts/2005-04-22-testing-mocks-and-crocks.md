---
id: 107
title: 'Testing: Mocks and Crocks'
date: 2005-04-22T07:34:38+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=107
permalink: /testing-mocks-and-crocks/
categories:
  - SoftwareDev
---
In tests, objects can be placed in two categories:

* <b>"Crock" objects - Objects populated with dummy values and enshrined with dummy behaviour for the purpose of simulating an object that might be encountered in production.</b>
* <b>"Mock" objects - Objects pre-loaded with predictions about how they will be used, and responsible for throwing an exception as soon as it becomes apparent a prediction won't be met.</b>

I make the distinction because mock objects has entered that industry buzz-word state. It has been adopted as a name for the very practices that it was intended to supplement. That the name is so evocative is a testament to the [clever people](http://www.connextra.com/aboutUs/mockobjects.pdf) who introduced the concept. "Mock" is a lot more memorable than "endo-testing assertion class".

**Crocks have a place too. Especially for system testing, it can be useful to simulate external systems rather than try to connect to them directly.** You can plug and play here, wiring your application to use a mix of real systems and simulations, so as to simulate different conditions.

Also, **it can be useful to build up a "universe of crocks" for testing purposes**. A few prototypical instances of your classes to be used as test data. If you have user accounts, for instance, create a "joeTheSysadmin", a "sallyTheManager", and so on. This can work well in conjunction with mock objects. For instance, you can tell a mock to expect that "joeTheSysadmin" will be passed to it. The [ObjectMother](http://c2.com/cgi/wiki/ObjectMother)  pattern supports retrieval of Crocks.

If you practice true unit testing - isolating a single class, then mocks should form a key part of the testing strategy. The class should refer only to interfaces, and you wire the tests so that these interfaces are implemented as mocks rather than using other classes in your project. Pragmatism rules the day as always, and you might find yourself using a mix of interfaces and real classes. 

Some further clarification on mock objects:

* If use a tool like [JMock](http://jmock.org), you can easily create a mock and set up its expectations without hand-coding it. Indeed with the stubs() method, you can easily create Crocks as well - it lets you tell an object how to respond to a call, without setting up any expectations about whether the call will actually be made.
* **Mocking goes hand-in-hand with certain design concepts: [interface-implementation separation](http://c2.com/cgi/wiki?SeparateInterfacesFromImplementation),  [dependency injection](http://c2.com/cgi/wiki/DependencyInjection), [IOC/lightweight containers](http://www.theserverside.com/news/thread.tss?thread_id=29269), [law of Demeter](http://www.google.co.uk/url?sa=U&start=1&q=http://www.ccs.neu.edu/home/lieber/LoD.html&e=10129).** You don't have to, but it helps a lot, and mock objects have actually pushed the use of these concepts across the industry.
* **If you design test-first, you'll find that classes don't need to expose properties as much as normal design would suggest.** You won't have getters for every property because there simply aren't use cases that require them. **Without mock-objects, you'd need to expose those properties purely for testing, which is unfortunate because exposing properties adds clutter and increases risk.** With mock objects, you don't have to [test your objects by interrogating them](http://www.martinfowler.com/articles/mocksArentStubs.html). Instead, you can test how your object interacts with other objects.