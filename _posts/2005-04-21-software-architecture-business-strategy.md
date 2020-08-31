---
id: 104
title: Software Architecture = Business Strategy
date: 2005-04-21T00:13:46+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=104
permalink: /software-architecture-business-strategy/
dsq_thread_id:
  - "375572187"
  - "375572187"
categories:
  - HumansAndTech
  - SoftwareDev
---
Clarke Ching notes that, contrary to popular belief, IT managers have a lot of influence on the business side - profits, strategy, etc. He explains why [agile processes make money for out customers](http://www.clarkeching.com/2005/04/software_develo.html). True. And as well as management, there's architecture, which is also important for business strategy. Whenever anyone influences the architecture, they're affecting business strategy, whether they acknowledge it or not.

So the techie - programmer or architect - might say:

> **"I don't care about strategy, paradigm shifts, and executive-level sushi! Data persistence, messaging protocols, devastating one-liners that make a sharp whooping noise every time there's a lunar eclipse? That I can take care of."**

**Actually, it's in the organisation's interests for technical decision-makers to know something about business strategy.** It doesn't have to be enough to influence it, and it doesn't even have to be too detailed, but it's a mistake to ignore it.

My thinking here is heavily influenced by [Software Architecture in Practice (Bass et al)](http://www.amazon.com/exec/obidos/tg/detail/-/0321154959/ref=lpr_g_1/002-6459916-1800848?v=glance&s=books).
**Design is all about making trade-offs, and this book delves into numerous case studies to illustrate how technical trade-offs are related to real-world strategy.**

Case in point: the web. Why did it succeed where previous attempts at hypertext failed? Because it's decentralised, so that it could scale up indefinitely. And it's error-tolerant. You don't have to write perfect HTML. Slight tangent here, but I have to add [this legendary quote from Philip Greenspun](http://philip.greenspun.com/panda/html):

> ... at least you already know how to write legal HTML:

> > My Samoyed is really hairy.

> That is a perfectly acceptable HTML document. Type it up in a text editor, save it as index.html, and put it on your Web server. A Web server can serve it. A user with Netscape Navigator can view it. A search engine can index it. 

OK, that's the web, a global phenomenon. How about in a single company? Again, some appreciation of strategy is vital.  What's our message to customers? Beyond the obligatory lip service, how much do we care about customers? Some companies have a very high regard for ongoing customer relationships, so IT system design should be aligned with that concern. That usually means optimising on usability and performance, and ensuring the helpdesk works smoothly, for instance. If customers are using different browsers or PCs, it might be necessary to support all of them.

**Other companies might care less about existing customers and more about new customer acquisition. Here, the concerns might shift towards more agile designs, so that new functionality can be more easily implemented.** Thus, we would no longer be concerned about support all the browsers and platforms, as that would slow us down in adding new functionality. ** This would be an optimisation towards flexibility at the expense of portability. **Business strategy has directly influenced technical decision-making.**

Yes, this is all very approximate. But the decisions are real. Whenever a choice is made for a web UI framework, or a persistence strategy, or even an overall architectural style, developers should be conscious of the  qualities  they are trading off. Flexibility, reliability, usability, performance, maintainability, understandability, testability, uptime, etc. And once you're aware of these qualities and you have to weigh up the pros and cons for a particular decision, you need some criteria to decide where the sweet spot lies. One solution might be particularly flexible, but not very reliable. And so on. The right way to pick an alternative is to think about which gives the best business value, and that comes from understanding whether, in this circumstance, how the business values each quality.

Finally, all this is relevant to any development process, not just agile. The implications will be different, e.g. more developers tend to make critical decisions in agile projects, and the decisions will usually be based on present needs rather than future speculation. And as a more general point, it makes sense for IT departments to support this dissemination of knowledge, again a strength of traditional agile projects. Nevertheless, the argument always holds: to deliver business value effectively, technical decisions-makers require an appreciation of business needs.