---
id: 1852
title: Canonical Feeds
date: 2012-10-22T11:57:46+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1852
permalink: /canonical-feeds/
categories:
  - SoftwareDev
---
I'm currently building some features to help manage series "aliases" on Player FM. The idea is to canonicalise podcasts, so there's only one true "TWIT" record in the system, for example. This is important for efficiency - it means the server's not parsing 12 different variants of the same feed. Moreover, it's important for user experience. It means we recognise when two users are subscribed to the same feed, so we can show them recommendations, they can share with each other, etc.

So we need aliases.

By aliases, I mean two things. Firstly, something like Wikipedia's redirects, e.g. a feed changes title from "foo" to "bar", now /series/foo will redirect to /series/bar. That's basically a slug alias. Secondly, there are "feed aliases". This is where a publisher [asks me](https://twitter.com/AskBryan/status/259027510526869504) to update the show's URL, perhaps because they've moved host. It may also be where a user or myself notices that a feed has changed, e.g. various people have recently been moving away from Feedburner, including 5x5 network, so I noticed their feeds are now marked "obsolete". So we'd like to alias the old feed to the new one, so anyone in the future who imports their XML containing the old feed will automatically be subscribed to the new one.

The aliases above are all database-driven. e.g. user subscribes to feed1.xml, we look it up in the aliases table and find it's aliased to feed2.xml, and boom...they're subscribed to feed2.xml. But a different kind of feed alias is an "automatic" one. By which I mean no DB...just some basic parsing rules. User subscribes to feedburner.com/AbC, we transform it to feedburner.com/abc, and boom they're subscribed to the same "abc" feed everyone else is subscribed to.

In the next post, I'll explain how Feedburner URLs work, since that's a big part of those automatic translations.