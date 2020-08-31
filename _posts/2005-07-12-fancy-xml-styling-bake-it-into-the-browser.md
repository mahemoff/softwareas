---
id: 159
title: 'Fancy XML Styling: Bake it Into the Browser'
date: 2005-07-12T03:42:25+00:00
author: admin
layout: post
guid: http://www.softwareas.com/fancy-xml-styling-bake-it-into-the-browser
permalink: /fancy-xml-styling-bake-it-into-the-browser/
dsq_thread_id:
  - "376375307"
  - "376375307"
categories:
  - HumansAndTech
  - SoftwareDev
---
There's a lot of talk about slapping XML stylesheets over RSS feeds. [A new oreillynet article](http://www.oreillynet.com/pub/a/network/2005/07/01/rss.html)  ([ta Mike Levin](http://jroller.com/page/Sandymountster/20050711#making_rss_pretty)) explains how. I guess this started with a few prominent sites like the BBC strutting their style, and now everyone's in on the act.

No doubt that it's much better for users, but it's unfortunate that individual developers have to set up their stylesheets - after all the bloggers <i>are</i> the users, and many of them simply can't or won't do it. I'm sure the various blogging toolkits will begin to incorporate it, but even then, **let the browser take care of these things!** It should certainly be in the interest of all browser manufacturers to increase the value of the web by introducing casual users to RSS.

It baffles me that browsers treat all XML files the same way. Even firefox:

> This XML file does not appear to have any style information associated with it. The document tree is shown below.

It's nice that the DOM is shown, legible and syntax-highlighted, but how about noticing the format and providing some helpful tips? **Why not keep an open repository of default stylesheets, one per known XML dialect?**