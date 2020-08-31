---
id: 76
title: Learning by Patterns using Patterns Within Patterns
date: 2005-03-23T13:30:36+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=76
permalink: /learning-by-patterns-using-patterns-within-patterns/
categories:
  - SoftwareDev
---
[Daniel Steinberg](http://weblogs.java.net/blog/editors/archives/2005/03/patterns_within.html):

> There are patterns within and among patterns for many of the original GoF design patterns ... A striking example is described in the latest column from Robert C. Martin's Principles, Patterns, and Practices series: [The Factory Pattern](http://today.java.net/pub/a/today/2005/03/09/factory.html). In it he shows that "Abstract Factory is just Strategy used for creating objects."

Yes, the original GoF patterns had many interesting relationships to each other. Many were noted in the book and many have been discussed since then. About a year ago, I created [this guide to learning the GoF patterns](http://mahemoff.com/paper/software/learningGoFPatterns/). One "trick" is to exploit the similarities to improve the learning curve, effectively compressing the quantity of concepts that must be learned. For instance:

> (6) **Command (233)** SIMILARITY: Command is almost identical to Strategy. That is, you call a "execute" method and the instance does it. The only difference here is Command "feels" more dynamic - it is, at some level, triggered by an external agent (e.g. an end-user). In contrast, a Strategy often represents a business rule, e.g. tax calculation. So the application may vary, but what actually happens is identical.

> (10) **Factory Method (107)** SIMILARITY: This pattern is just a special case of Template Method. As stated in the text, it applies only to Template Methods which involve the creation of an object. *Note that most people nowadays would have a different definition: a public creation method, typically of the class (or subclass) that the method belongs to.*

> (13) **Proxy (207)** Should be familiar to anyone who has used a web proxy.<br />
   (14) **Decorator (175)** SIMILARITY: Proxy is a special case of Decorator. It is worth learning Proxy first, because it a more familiar situation. Once understood, it is not so hard to see how a Decorator could wrap classes to perform tasks other than those performed by Proxy. Proxy is usually used with regard to security and networking, and typically a class with a proxy cannot be accessed directly. In contrast, a Decorator is usually used to enhance an existing class's functionality. A client can freely choose whether to wrap a class with its Decorator(s). As with the Strategy-Command relationship, Decorator shares the same mechanism as Proxy, varying only in the application area and style of use.