---
id: 1916
title: Testing HTTPS Locally
date: 2013-04-10T03:01:37+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1916
permalink: /testing-https-locally/
categories:
  - SoftwareDev
tags:
  - HTTPS
  - Pow
  - Rails
  - Security
  - Tunnels
---
As I'm migrating [the player](http://player.fm) over to HTTPS, one challenge is partial content, leading to an incomplete padlock and strikethrough domain warning like this:

![](http://i.imgur.com/Y23dq7c.png)

And the harsh but fair warning, upon inspection: "However, this page includes other resources which are not secure. These resources can be viewed by others while in transit, and can be modified by an attacker to change the look of the page."

![](http://i.imgur.com/k8vUT1E.png)

So to fix this locally, a nice setup for Ruby/Rails devs is [Pow](http://pow.cx) + [Tunnels](https://github.com/jugyo/tunnels). Both are super-simple to setup.

Pow is a local server, so if you usually run Rails on http://localhost:3000, you can one-click install Pow and all you need is to symlink your Rails folder to ~/.pow. Then you have a local server, sans port, like http://player.dev. Then, just install Tunnels and it will simply pipe https://player.dev into http://player.dev.

Now you can open Chrome devtools' resource tab and fish out any connections which are still https. Ideally host them locally, or at least change the links to https ones at possible loss of cache performance. Still, did you see various posts recently about ISPs injecting crapware script tags into people's pages? [OMG](http://arstechnica.com/tech-policy/2013/04/how-a-banner-ad-for-hs-ok/) [I know right!](https://news.ycombinator.com/item?id=5482178) Seriously, https-everywhere is where the web is heading. Even public sites aren't immune.