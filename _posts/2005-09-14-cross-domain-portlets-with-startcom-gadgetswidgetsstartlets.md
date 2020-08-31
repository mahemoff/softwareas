---
id: 199
title: Cross-Domain Portlets with Start.com Gadgets/Widgets/Startlets
date: 2005-09-14T08:37:10+00:00
author: admin
layout: post
guid: http://www.softwareas.com/cross-domain-portlets-with-startcom-gadgetswidgetsstartlets
permalink: /cross-domain-portlets-with-startcom-gadgetswidgetsstartlets/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375140737"
  - "375140737"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - DHTML
  - Javascript
  - Links
  - Patterns
  - Search
  - Software
  - Start.com
  - Web
  - Web 2.0
---
Scott Isaacs on a new [Start.com](http://start.com) feature (quoted on [Ajaxian](http://www.ajaxian.com/archives/2005/09/startcom_a_prev.html)):

> DHTML-based Gadgets: Start.com consumes DHTML-based components called Gadgets. These Gadgets can be created by any developer, hosted on any site, and consumed into the Start.com experience. The model is completely distributed. You can develop components derived from other components on the web.

**Remote portlets take the [Ajax portals](http://ajaxpatterns.org/Ajax_Examples#Portal) to another level. In fact, the whole concept is one of the biggest developments in the history of the web. [A9](http://a9.com) pre-empted it with their ["Open Search"]([http://opensearch.a9.com/) capability, which allows developers to hook into the A9 interface with live search results. Now MS is going a step further, with Konfabulator-style interaction directly on the web.** It's likely Yahoo has similar plans, given that it's now the owner of Konfabulator. What Google does is anyone's guess. **Strategically, MS has a big edge here because of its experience working with [Developers, Developers, Developers!](http://www.softwareas.com/the-story-behind-developers-developers-developers) (YES!)**

**The idea combines [Cross-Domain Mediator](http://ajaxpatterns.org/Cross-Domain Mediator) with [Portlet](http://ajaxpatterns.org/Portlet).** Those patterns have subsumed a now-deleted pattern that previous covered [this kind of thing](http://ajaxpatterns.org/wiki/index.php?title=Main_Page&oldid=1215):

**Cross-Domain Portlet:** Introduce Interactive Portlets to facilitate a conversation between the user and a third-party, e.g. for services or "advertising as conversation" (http://radar.oreilly.com/archives/2005/05/remaking_advert.html)

**Ajax makes it possible because there's no page refresh. Conceptually, each portlet is autonomous and capable of conducting a conversation with another domain in parallel with other portlets. When a result comes back to one portal, the other portlets are unaffected. (You can obviously yoke portals together if you want to.)** In practice, there are a couple of finer implementation points:

* You can't make an [XMLHttpRequest Call](http://ajaxpatterns.org/XMLHttpRequest_Call) to  an external domain. Hence, the portal server must mediate.
* Conducting parallel conversations, you'll need some form of [Call Tracking](http://ajaxpatterns.org/Call_Tracking). Hopefully, you're using a [library](http://ajaxpatterns.org/Ajax_Frameworks) that abstracts those details from you.

Now that a happening, here are a few things I'd like to see:

* **An open standard** for conducting cross-domain conversations, one that protects the end-user and the portal host, but provides sufficient functionality to the 
* **Useful ads** (the [advertising as conversation](http://radar.oreilly.com/archives/2005/05/remaking_advert.html)) concept. There's definitely a business model here for opt-in advertising. That is, users would be willing to add advertising portlets that offer genuinely useful information. e.g. a travel portlet that lets you check flight availability.
* **RSS aggregator integration** The nature of  a portal can change, right? So RSS aggregators should be able to include remote portlets.
* **End-user-created portlets.** Make it easy for end-users to construct their own gadgets. This idea is inspired by Charlene Li's comments on Konfabulator: "The problem is I already know what the ultimate widget would be me ... Thereâ€™s only one small problem -- I donâ€™t know JavaScript! So I am at the mercy of app developers ..."