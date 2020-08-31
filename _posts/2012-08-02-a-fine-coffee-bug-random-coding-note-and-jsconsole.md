---
id: 1794
title: A Fine Coffee Bug (Random Coding Note). And jsConsole.
date: 2012-08-02T17:28:51+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1794
permalink: /a-fine-coffee-bug-random-coding-note-and-jsconsole/
categories:
  - SoftwareDev
tags:
  - Debugging
  - Javascript
  - jsConsole
  - Mobile
---
This is a bug that took so long to track down, I had to write it somewhere.

The wrong code was:

<code>radio('new-page').subscribe = -> # handle new pages</code>

It should have been

<code>radio('new-page').subscribe -> # handle new pages </code>

The first call was actually over-writing the radio subscribe() function, so no further handlers were actually getting registered.

This does happen quite a bit with CoffeeScript. By wiping out all the parentheses and other junk, it leaves just a few symbols which sometimes are necessary and sometimes not. e.g. with jQuery onclick registration (`$('button').on 'click', -> ....`), one has to stop and think if there's a comma or not. Everything else is natural it flows staight from the lizard brain and onto the screen, but not the damn comma. Hopefully there will be some nicer syntax highlighters and run-time diagnostics to catch this kind of thing in the future.

What phased me about this was it was working on desktop, but not Android. Thought it might be some Android quirk. But it's because I've customised the basic player for android, so this code was only actually executed for Android.

Anyway, if there's one useful thing I can say about this: Remy's [jsConsole tool](http://jsconsole.com/) rocks! Seriously. It helped me get Player FM working on Windows Phone IE the other day and it got me out of this fine Android pickle today. With Android Browser, you can get a basic console with about:debug, but it's rubbish. Silently fails a lot of the time, only shows the first console log argument, no command-line history or completion so you're typing like it's a 2003 SMS. jsConsole makes it real easy. Just put something like this in your HTML layout (for Rails/Haml):

<code><pre>
 -if Rails.env.development?<br/>
   &lt;script src="http://jsconsole.com/remote.js?myawesomeapp"&gt;&lt;/script&gt;
</pre></code>

Then visit [jsConsole](http://jsconsole.com/) and type `:listen myawesomeapp`. Now you have a grown-up's console.