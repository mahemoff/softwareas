---
id: 1671
title: 'Announcing Player FM: Podcasts in Your Browser'
date: 2012-05-09T18:33:07+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1671
permalink: /announcing-player-fm-podcasts-in-your-browser/
categories:
  - Uncategorized
---
I've launched [Player FM](http://player.fm) today, a product I've been wanting to make since podcasting began in 2005! It's a way to discover, share, and play podcasts in the browser. Works pretty well in mobile browsers as well as the desktop.

<a href="http://player.fm"><img src="http://i.imgur.com/5J1Ae.png" alt="" title="Hosted by imgur.com" /></a>

Learned a ton in building this thing! A few technologies in here:
* Rails 3.1 on the server
* Twitter Bootstrap and Font Awesome icons
* HAML, SASS+Bourbon, CoffeeScript
* HTML5 history to keep playing while the user browses
* SoundManager 2 using Flash and falling back to HTML5 audio as appropriate
* RSS, JSON, OPML, and plain-text imports and exports

Any ideas for this, let me know. Hope it's useful!