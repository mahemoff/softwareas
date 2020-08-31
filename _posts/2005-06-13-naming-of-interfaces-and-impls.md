---
id: 147
title: 'Naming of Interfaces and Impl&#8217;s'
date: 2005-06-13T23:24:11+00:00
author: admin
layout: post
guid: http://www.softwareas.com/naming-of-interfaces-and-impls
permalink: /naming-of-interfaces-and-impls/
aktt_notify_twitter:
  - 'yes'
  - 'yes'
dsq_thread_id:
  - "375483777"
  - "375483777"
categories:
  - SoftwareDev
---
Cedric on Interface naming convention:

> >    <reader comment> Some argued that using 'I' adds noise. Usage of 'Impl' suffix takes care of this problem too.

> I wonder if the author of this remark noticed the irony of this comment :-)

Neeraj Kumar left a good comment on this, which is similar to what I was thinking: Both "I*" and "*Impl" add noise - the question is which one is less evil.

Here's why I prefer "*Impl".

<li> **The interface is part of the core code.** Using a container like Spring, implementations are hidden away in config. So "*Impl" is less invasive than "I*". 
<li><b>Both sound clumsy, but "I*" sound clumsier to me, mainly because the "I" dominates the start - rather than the end of the word</b>. I can think of "CoffeeMakerImpl" as "CoffeeMarkerBlahBlah", but it's harder to think of "ICoffeeMaker" as "BlahCoffeeMaker" - the initial "I" is too invasive.
<li> Furthermore, **it's easier to search for "*Impl" than "I*" in an IDE**, especially when some code will use the "I*" convention and other code won't (ie most external/legacy code).

**Actually, I usually prefer Impl's to tell me what kind of Impl.** Even if there's only one Impl, it's sometimes useful to provide a hint about what other Impl's might be possible. To use the canonical example, **I'd rather see BubbleSortImpl than SortImpl**. Also worth noting that if you're doing TDD, you probably have mock implementations as well; with JMock, they're not defined classes because they're instantiated using dynamic proxy. However, they are present, so I like to keep in the back of my mind that **the class name "XImpl" is really shorthand for  XProdImpl**.</reader>