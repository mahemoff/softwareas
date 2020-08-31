---
id: 663
title: 'InfoBoxPlugin: A TiddlyWiki Plugin for InfoBoxen'
date: 2009-10-07T02:04:12+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=663
permalink: /infoboxplugin/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574468"
categories:
  - SoftwareDev
tags:
  - Javascript
  - Osmosoft
  - Project
  - TiddlyWiki
---
<a href="http://www.flickr.com/photos/37184970@N00/3988151619/" title="InfoBoxPlugin - Lists tiddlers in a table (by mahemoff)"><img src="http://farm4.static.flickr.com/3515/3988151619_77bfa158d4.jpg" title="InfoBoxPlugin - Lists tiddlers in a table (by mahemoff)" alt="InfoBoxPlugin - Lists tiddlers in a table (by mahemoff)" width="400" height="627" /></a>

G'Day, here's a new tiddlywiki plugin I've been working on: <a href="http://tiddlywiki.mahemoff.com/InfoBoxPlugin.html">InfoBoxPlugin</a>. It's based on the equally-monikered infoBox in MediaWiki/Wikipedia, which you'll see in any article that is marked "current event" or "controversial", for example, on the big W. I find infoBoxes elegant, as they are unobtrusive enough to let you get on reading the article, and are easily ignored in the same way as <a href="http://www.useit.com/alertbox/banner-blindness.html">web ads</a>, but when you do focus on them, they are clear in meaning and support pattern recognition, with each type of infoBox having its own look and distinct icon.

The infoBox macro makes infoBoxen that look as shown in the diagram above. In the simplest case, you type this into a tiddler:

&lt;&lt;infoBox&gt;&gt;This is good stuff - pay attention mkay.&gt;&gt;

Pretty straightforward. One funniness here is the bracket asymmetry. We're trying to do something similar to XML tags, what with their start tag and attribs, followed by body, followed by closing tag, so you'd expect to see:

&lt;&lt;infoBox&gt;&gt;This is good stuff - pay attention mkay.&lt;&lt;/infoBox&gt;&gt;

or sumptink like dat. But one of my lessons was that tiddlywiki has a somewhat unusual convention, enshrined only in the gradient macro to my knowledge, for the former syntax. The only way to do something else would be to refactor or replicate or hijack the core code, and I don't fancy it, and in any event it would go against the standard already set by gradient. In any event, I was pleased enough when Jeremy showed me the example of the gradient tag, which shows that this kind of "macro body" is even possible, so I settled with that.

Okay, so that's nice, you can do a simple message, but where it gets more to the point is where you build up a family of infoBox types for your TiddlyWiki, each having a separate definition tiddler. For example, you will often want a "warning" infoBox to appear in various places. So you make a "warningInfoBox" tiddler, with the following text:

<pre>
|background|#fdd|
|borderColor|#f66|
|headingColor|#800|
|heading|Danger, Will Robinson!!!|
|messageFontStyle|normal|
|messageColor|#900|
|message|Please follow these instructions carefully.|
|iconURL|icons##stop|
|iconWidth|40|
</pre>

And then in a tiddler, you just write &lt;&lt;infoBox warning&gt;&gt;&gt;&gt; The association between "warning" and "warningInfoBox" is an enforced convention; my macro just appends "InfoBox" to the type you declare. The double-double closing bracket is a consequence of what I said above, combined with the fact that the definition has a pre-defined "message". This is often going to be what we want, but not always. In fact, all of the fields above are optional, so you could leave out "message" and then the warning macro would have to specify it (if you wanted a message, that is). i.e. &lt;&lt;infoBox warning&gt;&gt;This Is Serious Mum.&gt;&gt; (... because the undeniably-talented, always-controversial, Aussie band This Is Serious Mum - aka TISM - popped into my head as an instructive example for this warning.)

<h3>Some other things to say</h3>

* This plugin is part of a greater effort to pull out the goodies from TiddlyGuv into reusable modules. TiddlyGuv was the first thing I worked on upon joining Osmosoft, and when I looked it at with fresh eyes recently, I realised how much of what I built is just generic TiddlyWiki functionality. I now have a better understanding of what makes an independent TiddlyWiki plugin, and indeed I have a much greater respect for the whole modularity concept in TiddlyWiki, because it really satisfies all the traditional software engineering principles of encapsulation, orthogonality, etc etc in a neat bite-size way, which I will have to explain more about elsewhere. infoBox is the first of several plugins that need to be exorcised from the TiddlyGuv base.
* The "macro body" thing is actually quite easy - you just call <tt>wikifier.subWikify(domEl, "&gt;&gt;");</tt> where domEl is some DOM element. This will keep reading from the end of the macro definition to the next occurrence of &gt;&gt;, and fill domEl with the results of wikifying that content. It would be nice if there was a function to let you just get the string, instead of sticking it in the DOM, but you could still achieve that yourself by shoving it into a hidden element and capturing its innerHTML. The only complication for me was a common one these days of jumping between JQuery-land and traditional DOM-land, since TiddlyWiki now ships with JQuery, but much of the infrastructure has not (yet) been retrofitted to talk JQuery. Once I did a JQuery-to-DOM conversion, it worked fine.
* Another interesting detour that happened here concerned cross-referencing tiddlers. Something you will want often want to do with infoBoxes is use icons. In a single-file TiddlyWiki, often intended to be offline, the icons would need to be data: URIs. This applies to other plugins too, so I dedcided to look into it a bit. I wanted a way for the "iconURL" slice in the InfoBox definition to either be a regular URL, or a reference to another tiddler containing the data: URI, so as to isolate it away. This led me to learn more about <a href="http://groups.google.com/group/tiddlywikidev/browse_thread/thread/91e2b4bdc82cb8bd">transclusion</a>. With thanks to @FND, and after some experimentation, I found the easiest way was to support linking to sections of another tiddler. See how it works in <a href="http://tiddlywiki.mahemoff.com/InfoBoxPlugin.html">the demo tiddlywiki</a>, where an "icons" tiddler contains the data:URI icons.

Wow, I didn't expect to say so much about what is not a major plugin. It comes at a time when I've been making some realisations about tiddlywiki, hence the verbeage.
