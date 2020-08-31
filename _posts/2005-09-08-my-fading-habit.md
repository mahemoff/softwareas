---
id: 193
title: A Fading Habit
date: 2005-09-08T19:09:56+00:00
author: admin
layout: post
guid: http://www.softwareas.com/my-fading-habit
permalink: /my-fading-habit/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572526"
  - "375572526"
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
  - Software
  - Web
  - Yellow Fade Technique
---
**I've noticed that I've recently habitualised the [Yellow Fade Technique](http://www.37signals.com/svn/archives/000558.php), or what the Ajax patterns refer to as [One-Second Spotlight](http://ajaxify.com/One-Second_Spotlight).**

**The typical Fade example is a form field. When you change it, the field is suddenly highlighted, then gradually fades back to its original form. This tells the user that "the computer" knows something's happened, and also serves to draw their attention to a particular element.**

This is one of those things that could have been big years ago, but never happened. Despite the fact it's only become popular recently, it's all quite simple from a technical perspective, even more so with the new libraries coming out. I created a couple of demos a while back - one is powered by [Scriptaculous](http://script.aculo.us),
the other uses a custom-built fading engine. The [first demo](http://www.ajaxify.com/run/time/periodicRefresh/spotlightScriptaculous/) runs opacity through a sequence, the [second demo](http://www.ajaxify.com/run/time/periodicRefresh/spotlightCustom/) does the same to colour, rather than opacity.

In the Scriptaculous case, running the effect is mind-numbingly simple to invoke:
> new Effect.Appear("defaultTimeLabel");

And likewise in the case of my custom fader (which lets the user specify colour preferences):

>  fader.fade(defaultTimeLabel, $("startColor").value, $("endColor").value);

Anyway, **I've lately been coding some more dynamic DOM manipulations, and it's occurred to me that I now ask myself, whenever I add or remove an element, if I need to run an effect. Having scriptaculous handy makes it so easy to do.** So fading started off as a bit of a novelty and is now standard practice.

I can hear people saying, "not the blink tag" and re-living 1995-esque motion sickness. That will definitely happen on some Ajaxian sites, but let me clarify that I'm only asking the question each time a change comes up, not actually implementing the change. Apps using the <a href="http://ajaxpatterns.org">One-Second" visual effects </a>  include [TiddlyWiki](http://tiddlywiki.com) and [Backpack](http://backpackit.com) (one of the first uses). They show how it can be used effectively and without going overboard.

Of all the new JS libs coming out, I haven't seen any that augment or replace basic XHTML DOM manipulation. If one does emerge, I'd like to see it provide support for auto-effects and perhaps a parameter to indicate the effect. e.g. <tt>el.hide(Effect.FadeOut); el1.add(el2, Effect.BlindDown).</tt>
