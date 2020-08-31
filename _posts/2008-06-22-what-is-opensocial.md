---
id: 454
title: What is OpenSocial?
date: 2008-06-22T19:31:06+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=451
permalink: /what-is-opensocial/
dsq_thread_id:
  - "375573764"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Gadgets
  - Google
  - OpenSocial
  - Web
  - Web 2.0
---
I just realised there's no good executive summary for OpenSocial. Every resource fluffs about the "social" aspect and forgets about the UI aspect. <strong> The UI aspect, essentially a gadget specification, is just as important as the social aspect, notwithstanding its absence from the "OpenSocial" brand name</strong>. I'm not a fan of the name "OpenSocial" for this reason, though I acknowledge it does have more attention-grabbing bling than "open social widget framework 1.0". In any event, it's regrettable that most commentators gobble it up hook, line, and sinker; as evidenced by their almost exclusive focus on the social angle.

With no further ado, here's my attempt at a one-paragraph summary of OpenSocial ...

<h3>OpenSocial Executive Summary</h3>

OpenSocial is a standard for "mini" web apps, called "gadgets", which are designed to be embedded other websites. The standard informs developers who wish to write portable gadgets, i.e. those which work in any OpenSocial environment; and likewise, it informs developers who are creating such environments. It  defines an XML format for applications, typically containing the user interface (HTML/CSS/Javascript) as well as metadata, e.g. author, gadget size, and preferences. In addition, OpenSocial defines a number of APIs, so that gadgets can invoke services such as changing the gadget height and fetching remote content. One particularly important class of APIs are those of a social nature. These enable a gadget to access data and run services related to the user who is viewing the gadget, or the user whose web page the gadget is embedded in. For example, the gadget can - subject to security settings - find a person's name and location, traverse their social network, and invite them to install an application. Access to social data is not limited to gadgets, however, as OpenSocial also provides a RESTful variant of the social API, suitable for any kind of net-enabled client. OpenSocial was launched by Google in November, 2007, and is to be managed by the non-profit OpenSocial Foundation.

<img src="http://picupper.com/2008/04/16/opensocial.jpg" width="200" height="200" />