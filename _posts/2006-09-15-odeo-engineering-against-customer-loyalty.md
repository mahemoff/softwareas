---
id: 343
title: 'Odeo: Engineering Against Customer Loyalty'
date: 2006-09-15T07:41:11+00:00
author: admin
layout: post
guid: http://www.softwareas.com/odeo-engineering-against-customer-loyalty
permalink: /odeo-engineering-against-customer-loyalty/
dsq_thread_id:
  - "375573092"
categories:
  - SoftwareDev
tags:
  - Odeo
  - Podcasts
  - Web2.0
---
<a href="http://software.gigaom.com/2006/09/14/evan-williams-how-odeo-screwed-up/">GigaOM discusses "How Odeo Screwed Up"</a>. Odeo is a service I want to like. I promoted it to others when it came out and I frequently use it as an example of the <a href="http://ajaxpatterns.org">Richer Plugin</a> pattern as it uses an effective combination of Flash and Ajax.

However, I had to stop using Odeo six months ago, due to an astounding oversight in their central architecture for doing what they are meant to do best: manage podcasts. The problem is simply that <b>Odeo places all podcasts into a single RSS feed</b>. You can probably imagine the consequences.

<a href="http://odeo.com"><img width="400" height="200" src="http://img176.imageshack.us/img176/8011/odeokr6.png" /></a>

The feed inevitably grows and grows, and suddenly you have 5000+ multimedia items for your podcatcher to fetch and sync. ITunes simply gives up. Juice/IPodder hangs for about 30 minutes and might then start updating if the stars align with the moon. Under some circumstances, like after a (likely) crash leading to a corrupt record of what you're downloading, Juice will start downloading all 5000 podcasts.

So the architecture is kind of flawed from the get-go. A single ever-growing feed. What tools does Odeo offer to tame it? Well, you can manually chop the beanstalk down one podcast at a time. This used to be rather difficult because of overzealous use of a <a href="http://ajaxpatterns.org/One-Second_Spotlight">Yellow Fade Effect</a>, which meant you could only delete an item every two seconds or so. Now, Odeo offers a checkbox-driven interface, but you must still manually click on each checkbox, you only have 25 checkboxes per page, and there's no keyboard shortcuts possible in Firefox AFAICT. So still unpractical. And the beanstalk keeps growing as you slowly chop it down at the other end.

<b>What's blatantly obvious is that Odeo needs an auto-delete feature, e.g. delete feeds older than 1/3/7/30 days</b> or keep a maximum of 10/100/1000 podcasts in your feed. It's such an obvious thing, it's almost breathtaking that it doesn't exist. I keep double-checking as I write this, but the fact is that <b>I've previously mailed support about it and there's no such feature</b>. I don't really understand what's going on, as it's hardly a niche request; it's something that affects every users. 

Odeo will work fine for new subscribers, but as soon as you've been subscribed for a few months, it's impossible to use. I mean <i>impossible</i>! As I say, I like the website a lot and I wish there was a way to get it working. But it's simply not possible. Way to encourage loyalty! <b>I can understand when this happens with a small startup, but Odeo is high-profile, VC-funded, and continues to roll out completely orthogonal products like Twitter, Hellodeo, and podcast recording.</b> Meanwhile, their core feature has remained impossible to use for twelve months!

The GigaOM article points to an interview which illuminates how these problems have come about. (<i>Note: updated the list numbering from the original article.</i>)

<blockquote>
Williams went through a tidy list of the top five Odeo screw-ups:

1. â€œTrying to build too muchâ€ â€“ Odeo set out to be a podcasting company with no focus beyond that.

2. â€œNot building for people like ourselvesâ€ â€“ For example, Williams doesnâ€™t podcast himself, and he says as a result the companyâ€™s web-based recording tools were too simplistic.
</blockquote>

The first point highlights that Odeo might be better off looking at why subscribers like me have stopped using it. I realise they are probably building services like Twitter to produce a better revenue stream, but why throw away core users?

<b>The second point makes me wonder how many Odeo staffers actually use Odeo at all, let alone to create podcasts.</b> Like I say, Odeo has an unusual property for a website, in that it virtually forces you to give up after using it for several months. Maybe the internal staffers rely on cron-powered SQL delete commands to flush their feeds, but there appears to be no solution for the rest of us.

I want to use Odeo again. Please let me know if anyone has a solution to the Amazing Indestructible Odeo Feed That Knows No Satiety.<!--374da728a4ddd7b02c94fc9d3ab56178-->