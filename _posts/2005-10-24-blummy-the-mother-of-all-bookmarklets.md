---
id: 222
title: 'Blummy: The Mother of All Bookmarklets'
date: 2005-10-24T07:37:40+00:00
author: admin
layout: post
guid: http://www.softwareas.com/blummy-the-mother-of-all-bookmarklets
permalink: /blummy-the-mother-of-all-bookmarklets/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572653"
  - "375572653"
categories:
  - HumansAndTech
  - Links
tags:
  - AjaxPatterns
  - Blummy
  - Bookmarklet
  - DHTML
  - Javascript
  - Links
  - Patterns
  - Portal
  - Software
  - Web 2.0
---
**Check out Alexander Kirk's new website: [Blummy](http://blummy.com). A blummy is a kind of bookmarklet that opens up a kind of [pop-up](http://ajaxpatterns.org/Popup) portal, giving you access to various web services.** Just like a portal is made up of [Portlets](http://ajaxpatterns.org/Portlet), a Blummy is made of Blummlets, which essentially do the kind of things bookmarklets do.  e.g. A blummlet can let you subscribe to this page with Bloglines, change the browser location, or show an image. Where the blummlet is interactive, the action takes place within the popup as a [Live Form](http://ajaxpatterns.org/Live_Form).

Here's a few interesting things about the site:

* **Because the Blummlet lives in a bookmarklet, XMLHttpRequest can access any domain.** Scott Isaacs [recently](http://spaces.msn.com/members/siteexperts/Blog/cns!1pNcL8JwTfkkjv4gg6LkVCpw!2332.entry) [suggested](http://spaces.msn.com/members/siteexperts/Blog/cns!1pNcL8JwTfkkjv4gg6LkVCpw!2085.entry)  it would be worth the risk for browsers to drop the same-domain policy, though it's unlikely to happen  anytime soon. A bookmarklet, I'm guessing, gets around that constraint.
* **The site lets users share Blummlets, which might lead to Cross-Site Scripting (XSS) attacks like [the now-famous myspace effort](http://blog.outer-court.com/archive/2005-10-14-n81.html)**. Alexander's well aware of this risk, which is why there's a "Report Concern"  checkbutton. It will be interesting to see how this kind of moderation works out. I still think users might need something stricter, like a whitelist approach, where Blummlets have to be explicitly approved by "the community", i.e. guilty until proven innocent. (This is still vulnerable, but I think it's a better trade-off overall.)
* **There are shades of [yubnub](http://yubnub.org) here, as well as the [widget/gadget/startlet idea](http://www.softwareas.com/cross-domain-portlets-with-startcom-gadgetswidgetsstartlets) seen on [start.com](http://start.com).** Leading to a repository of Blummlets. I mentioned to Alexander it would be nice to see an RSS feed, where users could somehow drag or a Blummlet into their existing Blummy.
* Speaking of gadgets/widgets, **the popup feels something like Dashboard and Konfabulator. Another example of [tha Ajax Desktop](http://softwareas.com/the-ajax-desktop), and a pretty useful one in this case.** There are various popup bookmarklets like [JSCalc](http://www.themaninblue.com/experiment/JSCalc/), which offer one particular function. They are convenient , but there's no central management point, and a lot of duplication and inconsistency in how the manage the popup experience. So Blummy does to the browser what Dashboard does the windows system: provide a common structure for individual applets. I haven't looked into the programming model, but there's probably good scope for a JS util library to further facilitate Blummlet development.