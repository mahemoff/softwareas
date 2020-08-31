---
id: 185
title: Ajax Periodic Refresh, Chat, and Multiplayer Gaming
date: 2005-08-27T16:38:23+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-periodic-refresh-chat-and-multiplayer-gaming
permalink: /ajax-periodic-refresh-chat-and-multiplayer-gaming/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375263556"
  - "375263556"
categories:
  - HumansAndTech
  - Links
tags:
  - AjaxPatterns
  - Chat
  - DHTML
  - Games
  - InstantMessaging
  - Javascript
  - Links
  - Messaging
  - Patterns
  - Software
  - Web
---
First, a quick update on [yesterday's book anouncement](http://www.softwareas.com/ajax-design-patterns-book): Thanks for your interest. Yes, it will be published as a physical book. In the O'Reilly animal format. And no, I don't know which animal.

**[Periodic Refresh](http://ajaxpatterns.org/Periodic_Refresh) is a pattern where the page runs a loop to continuously grab fresh data from the server ([Ajaxify Time Demo](http://ajaxify.com/run/time/periodicRefresh/)).**

As that pattern explains, **there are quite a few chat systems that work that way**. And a slashdot poster pointed out that many Japanese chat apps worked the same way in the late-90s, albeit with full page refreshes instead of [XMLHttpRequest](XMLHttpRequest Calls), because the web handled the character set better than desktop GUIs.

**When I first heard of [Google Talk](http://www.google.com/talk/), I thought "Hello, Google's doing Ajaxian chat". But, no, the text/IM component for now is a windows-only Jabber client.** There's a great opportunity for a hybrid approach here - provide a rich client which will stay on 24x7, pop up when a message occurs, and show an appropriate icon in the system tray, and also provide a web client which can be used wherever you are. **Google is well-placed to do it because (a) they certainly know how to Ajaxify; (b) they *need* to Ajaxify - windows clients are fine and dandy, but in order to sustain its advantage, Google has to change the rules of the game by establishing the web as the platform, not the desktop; (c) Periodic Refresh is expensive because frequent requests must be handled and Google, well, they can take the hit better than most.**

So in a way, I feel like Google's missed a trick here (but then, you can never be sure what they have up their sleeves). There's already **JWChat, an open-source [Ajaxian Jabber Client](http://jwchat.sourceforge.net/index.shtml)**. While JWChat's demo is really just a demo, I wouldn't be surprised to see someone picking it up and creating a serious public website based on it. **Meanwhile, there are offerings like [QWAD Chat](http://www.qwadchat.com/) which are taking the business model for Ajaxian chat very seriously.**

Yesterday, another [interesting announcement](http://groups.google.co.in/group/ajax-web-technology/browse_thread/thread/91d9d38cfdc1a272):

> We are working on an open source project to develop a peer to peer graphical adventure game, using AJAX!
> Looking for AJAX developers of any skill level who want to pitch in and help out!
> Interested? Download the first version (single player) at http://www.p2pmud.com 

**With Periodic Refresh, Ajaxian multi-player is feasible.** I'm curious to see how far it can go. There's a few [game examples](http://ajaxpatterns.org/Ajax_Examples) already, including Crisp's stupendous [DHTML Lemmings](http://crew.tweakers.net/crisp/lemmings/) effort. In their inaugural [Ajaxian podcast](http://www.ajaxian.com/archives/2005/08/ajaxiancom_laun.html), the Ajaxians discuss SVG, which is finally about to become a reality on Firefox 1.1. Combine SVG with [Periodic Refresh](http://ajaxpatterns.org/Periodic_Refresh) and we'll be gaming like it's 1995. (But without the sound effects. Playstation and X-Box have nothing to fear.)

As an aside, a thread a while back on Google Groups discussed whether unique URLs are worthwhile for Ajax apps. The argument was, why bookmark your state within an app?  Of course, one answer is that you want to bookmark a particular object, like a location in Google Maps. But, when you think about it, why not bookmark the state in an app. I mention this because it would be sweet if you could have a unique URL for a position in a game. So you just bookmark it instead of saving it or you can mail it to your mates.

As another aside, I'm glad Google Talk went with Jabber and I hope they really do move to SIP for voice as they've hinted. IM today is popular, but it could easily have been ubiquitous by now if not for the fragmentation caused by AIM/ICQ/MSN/Yahoo/IRC/Jabber splitting the market, thus exponentially dropping the value of using a given solution. Now, voice has skype, Gizmo (SIP-based), Google Talk, as well as the offerings from the IM incumbents.