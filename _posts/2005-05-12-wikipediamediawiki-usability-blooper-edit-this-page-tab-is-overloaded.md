---
id: 123
title: 'Wikipedia/MediaWiki Usability Blooper: &#8220;Edit This Page&#8221; Tab is Overloaded'
date: 2005-05-12T06:53:03+00:00
author: admin
layout: post
guid: http://www.softwareas.com/wikipediamediawiki-usability-blooper-edit-this-page-tab-is-overloaded
permalink: /wikipediamediawiki-usability-blooper-edit-this-page-tab-is-overloaded/
dsq_thread_id:
  - "376990513"
  - "376990513"
categories:
  - HumansAndTech
---
Tabbing is a simple mechanism, popularised by Amazon in the late 90s, for websites to support navigation.
[Wikipedia](http://en.wikipedia.org/wiki/Wiki) (or any [mediawiki](http://meta.wikimedia.org/wiki/Wiki)-powered site) uses a tab metaphor to break down a page into Article, Discussion, Edit This Page, History.  Which is more useful than other wikis that place these links in random and exciting places.

However, the Edit This Page tab is broken. If you're in Article, it edits the article. If you're in Discussion, it edits the discussion. It does say "Edit this Page", so it's an improvement on the raw "Edit" of the current mediawiki release, but consider the many new users of Wikipedia ... what's a "page"? The main content or what I'm looking at now.

The problem here is the metaphor doesn't work. A tab is metaphor for a physical space, and should therefore be stateless. You don't expect the contents of a physical space to change based on what you're doing right now. The result is a lack of predictability: the user is not quite sure what will happen when they click on the tab. Admittedly, the consequences are low. But it could stop a user editing content. If they were in the Discussion age and they wanted to change something, they might reasonably assume the Edit tab concerns the main page, and fail to find Edit for the discussion.

I'd suggest this:

* Split Article into two "Siamese Twin" tabs - "Article" and "Edit" tabs, in almost complete tab form, and joined at the hip. Minor risk that the user will misfire due to them being so close, but the gain in understandability is worth the trade-off.
* Or, if we really want to conserve the tab quantity, make it obvious that "Edit" is a magic tab ... use a slightly different shape and, in a different colour, show what will be edited when the user clicks on it. e.g. <font color="red">"Edit Discussion"</font>. If we're going to exploit the magic of computers to make the tab behave dynamically, it may as well look dynamic too.