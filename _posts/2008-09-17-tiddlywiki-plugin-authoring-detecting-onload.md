---
id: 485
title: 'Tiddlywiki Plugin Authoring: Detecting onload'
date: 2008-09-17T14:17:43+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=482
permalink: /tiddlywiki-plugin-authoring-detecting-onload/
dsq_thread_id:
  - "375573959"
categories:
  - SoftwareDev
tags:
  - Ajax
  - TiddlyWiki
---
<a href="http://softwareas.com/shout-first-tiddlywiki-plugin">Tiddlywiki plugins</a> load on startup, early on in the whole boot sequence. I was wondering how to detect when elements are on the page and got some good advice in <a href="irc://irc.freenode.net/tiddlywiki">#tiddlywiki</a>.

Turns out there's no hooks, but a kind-of-hook is macros' init() function. I didn't want to use this, since I'm not creating a macro, though it would have been possible to create a "fake" macro - ie one that's not intended to be called, but just does something in its init(). However, I went for the more general solution - hijacking (monkey-patching) restart():

[javascript]
var origRestart = restart;
window.restart = function() {
  origRestart();
  ... some code which can assume elements are on the page ...
}
[/javascript]

mmahemoff: hi, i'm writing a plugin that needs to load as soon as the page is ready...is there an event handler for that?<br/>
mmahemoff: specifically, my PageTemplate contains an element and I want my plugin to do document.getElementById("element")<br/>
Ace_NoOne: mmahemoff: well, there's a ticket for those kinda hooks - but no implementation so far AFAIK<br/>
Ace_NoOne: a hacky way would be to write a macro that's hidden in (executed by) some PageTemplate element<br/>
jayfresh: mmahemoff: there is this:<br/>
jayfresh: var startingUp = false;<br/>
jayfresh: that's in the global space and is true during main()<br/>
jayfresh: and false the rest of the time<br/>
Ace_NoOne: FWIW, <a href="http://trac.tiddlywiki.org/ticket/484">http://trac.tiddlywiki.org/ticket/484</a><br/>
Ace_NoOne: has some links<br/>
Ace_NoOne: specifically: <a href="http://trac.tiddlywiki.org/ticket/484">http://www.tiddlywiki.org/wiki/Dev:Startup_Phases</a>
mmahemoff: great tips, thanks :)<br/>
Ace_NoOne: mmahemoff: macros' init function run after refreshDisplay<br/>
mmahemoff: ok, that ought to do it in my case<br/>
mmahemoff: in the more general case, it sounds like hijacking restart() is the typical pattern?<br/>
Ace_NoOne: mmahemoff: saqimtiaz1 probably knows best<br/>
saqimtiaz1: mmahemoff: standard practice is to hijack restart. Not pretty but the best we have right now<br/>

(Snipped some discussion related to a separate thread.)