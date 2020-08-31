---
id: 1454
title: 'Nicholas Zakas: Scalable Web Architecture [Full Frontal Live Blog]'
date: 2011-11-11T15:20:15+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1454
permalink: /nicholas-zakas-scalable-web-architecture-full-frontal-live-blog/
dsq_thread_id:
  - "468553961"
categories:
  - SoftwareDev
tags:
  - Conference
  - Javascript
---
Nicholas Zakas is talking about scalable JS architecture.

He begins with a straw poll. Turns out half of the Full Frontal room is working
on a Single Page App, right now.

Framework != Library. jQuery? Not a framework. It's a library you call to
perform some limited functionality.

What's a "module"? Very overloaded term, but Nicholas wants us to think about a
module as a block of HTML, CSS, and JavaScript together. Like a widget on the
Yahoo! homepage. Modules should be loosely coupled, and this can be achieved
with the modules living in a sandbox.

Nicholas identifies a layered architecture, where an application core mediates between independent modules, which use a base library (jQuery etc).

Think of modules as little kids - they can do lots of cool stuff, but need
strict supervision:
* Hands to yourself (limiting what they can access)
* Ask, don't take
* Don't leave your toys around
* Don't talk to strangers

The Application core manages module lifecycles and mediates between them.
There's also an error handling role, and Nicholas gave a talk about this
previously: [JS Error
Handling](http://www.slideshare.net/nzakas/enterprise-javascript-error-handling-presentation).

People are usually too coupled to their base libraries, like jQuery. As Joe
Smarr pointed out in a 2007 talk, you're better off using them as scaffolding,
and building modules around them.

![img](https://lh3.googleusercontent.com/-fjJoDt9_QgU/Tr08ID6xRcI/AAAAAAAAAp8/R1RFOfGeLas/h301/11%2B-%2B1)