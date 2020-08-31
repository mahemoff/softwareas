---
id: 481
title: OpenSocial-Tiddlywiki Integration
date: 2008-09-03T11:19:34+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=478
permalink: /opensocial-tiddlywiki-integration/
dsq_thread_id:
  - "375573949"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Gadgets
  - OpenSocial
  - Osmosoft
  - TiddlyWiki
  - Web
---
<a href="http://www.btinternet.com/~tdroza/tiddlywiki/gadget.html">Go straight to the demo.</a>

<a href="http://www.btinternet.com/~tdroza/tiddlywiki/gadget.html"><img src="http://img.skitch.com/20080903-t1jkyn98k3rbj8mr6k5jc87c4c.jpg" style="width: 98%;" alt="Google Gadget TiddlyWiki plugin - a tiddlywiki macro to embed google/opensocial gadgets"/></a>

I'm at the Osmosoft hackathon and finally got an opportunity to experiment with <a href="http://opensocial.org">OpenSocial</a>-<a href="http://tiddlywiki.org">Tiddlywiki</a> integration. Specifically, how to embed OpenSocial gadgets in Tiddlywiki. I paired (trio'd?) up with <a href="">Stuart Race</a> and <a href="">Tom D'Roza</a> on it. We managed to get something useful up in an hour or two, which is testimony to the simplicity of both OpenSocial and Tiddlywiki. It's only proof-of-concept for now and for some reason doesn't work in IE.

Technically, it's iGoogle integration, not OpenSocial. The gadgets are iframes pointing to the iGoogle gadget server (gmodules.com). That's because right now, it's not clear there are any OpenSocial containers that will serve out gadgets externally in the same way. Of the various live OpenSocial containers, there is really scant information about how to embed the gadgets in an external page. Suffice to say, the code here is virtually identical to what you'd need to embed an OpenSocial gadget - it's simply a matter of changing the endpoint URL from whence gadgets are served.

One concern about this is whether or not Google will be cool with us pointing directly to the iframe. Technically, you're supposed to embed gadgets using a script tag, which will document.writeln() the iframe and its source. I vaguely recall a time last year where we were playing around with direct calls to the gadget, and gmodules saying no. This is possible in theory, if the server was attempting to match each iframe request with a previous corresponding script call. However, I am probably dreaming. It seems to be working fine. In any event, Shindig has no constraint like that, so if we extend this to point to other opensocial servers, or something spun up by an individual, it should work fine.

<h3>Usage</h3>

With the plugin installed, it's simple to use:

<code>&lt;&lt;gadget http://abowman.googlepages.com/spider.xml &gt;&gt;</code>

or with options:

<code>&lt;&lt;gadget http://www.btinternet.com/~tdroza/gadgets/twitter/index.xml height:400 width:500 border:0 prefs:"up_max_items=5&up_username=downingstreet&up_feed=http://twitter.com/statuses/user_timeline/" &gt;&gt;</code>

If you're familiar with opensocial you'll realise that the height, width, and border are options to the gadget server telling it how to render the gadget and its chrome; whereas the prefs string contains preferences which the gadget itself gets. All this is optional.

<h3>Plugin Code</h3>

We began with <a href="http://softwareas.com/shout-first-tiddlywiki-plugin">the Shout plugin whose code I've already documented</a>. It was only a matter of creating an iframe and pointing it - by setting its <tt>src</tt> property - to "http://www.gmodules.com/ig/ifr?url="+params[0]. And that worked fine, and we had gadgets inside tiddlywiki.

The hard part was parameters, took a little investigation to work out how to handle key-value pair parameters. The plugin code below serves as a simple example for how it's done. It's very similar to the very cool Ruby/Rails idiom which has also been adopted by Javascript libraries like Prototype (obviously, given its Rails association) and JQuery. i.e. mandatory params followed by a hash of optional params. Here, the URL is mandatory, and its proceeded by a set of key-value pairs.

The plugin code:

[javascript]
config.macros.gadget = {};
config.macros.gadget .handler = function(place,macroName,params, wikifier, paramString) {
var elem = createTiddlyElement(place,"iframe",null,"greeting","");
var p = paramString.parseParams(null, null, true);

elem.src= "http://www.gmodules.com/ig/ifr?url=" + params[0] + "&" + getParam(p,"prefs","");
elem.height = getParam(p,"height","200");
elem.width= getParam(p,"width","300");
elem.style.border= getParam(p,"border","1");

place.appendChild(elem);
}
[/javascript]

That's it.

<h3>Applications</h3>

Why would you want to embed a gadget in a tiddlywiki, aside from proof of concept? Well, tiddlywiki is a platform whose applications are many and varied; OpenSocial integration simply enhances the platform so that developers can select from a rich palette of existing gadgets. For example, if your tiddlywiki involves trip planning, pull in a Google Maps gadget.

It also makes for an extremely easy way to collect up a bunch of related gadgets, and optionally have a conversation around them. For example, you could compile your favourite game and toy gadgets into a game tiddlywiki. Remember tiddlywikis are single files, so this becomes a single file  game.html which you can mail around, keep on your hard drive, or post to a server. A related usage would be a single tiddlywiki where all gadgets are the same type, but with different preference strings. For example, 10 weather gadgets with different "location" settings.