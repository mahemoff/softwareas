---
id: 1383
title: WebWorkers, Cross-Domain JSONP, and CoffeeScript
date: 2011-10-07T12:43:57+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1383
permalink: /webworkers-cross-domain-jsonp-and-coffeescript/
dsq_thread_id:
  - "436755356"
categories:
  - SoftwareDev
tags:
  - Ajax
  - CoffeeScript
  - JSON
  - WebWorkers
---
Today's buzzword gotcha is brought to you by WebWorkers, Cross-Domain JSONP, and CoffeeScript.
TL;DR: Always use "self" for WebWorker "globals". And a library.

My Twitter app's locking the main thread a bit, so thought I could quickly push polling functionality into a WebWorker. Not so fast ...

Firstly, WebWorkers don't do JSONP the normal way. You can't inject a script because there's no DOM. This means you can't even use [standalone JSONP libraries](http://www.nonobtrusive.com/2010/05/20/lightweight-jsonp-without-any-3rd-party-libraries/), let alone jQuery (which doesn't even run in a WebWorker, as it assumes DOM presence, and would be a waste of bandwidth anyway).

[Fortunately](http://cggallant.blogspot.com/2010/10/jsonp-overview-and-jsonp-in-html-5-web.html), we can use importScripts(). Conveniently enough, importScripts() can be used anytime and accepts any old string. So the API would actually be useful in the main thread too, but I digress ...

So in Plain Old JavaScript, you would do:

[javascript]
function go() { doSomething(); }
importScripts("api.twitter.com?callback=go");
[/javascript]

Works just fine. But this won't work in the CoffeeScript equivalent, i.e.:

[code]
go = -> doSomething()  ### NOT CALLED
importScripts "api.twitter.com?callback=go"
[/code]

In fact, Chrome gives a mysterious error "Uncaught undefined", while Firefox cuts to the chase: "go is not defined".

The reason is that the CoffeeScript compiler wraps the entire thing in a closure. This is tremendously useful default behaviour, as you don't have to worry about adding new globals, but can cause problems in situations like this. If the script comes back from Twitter and calls "go()", where does that actually end up? With the main thread, a CoffeeScript can explicitly bust properties out of the closure using the global namespace, i.e. "window.foo" (or "global.foo" in the case of a server-side Node script). In fact, there's a solution to this with WebWorkers too. have their own global identity, "self".

[code]
self.go = -> doSomething()  ### FTFY
importScripts "api.twitter.com?callback=go"
[/code]

Works.

Be sure to use "self" for other WebWorker "globals" too, i.e.:

[code]
  self.onmessage = (ev) -> doSomething()
[/code]

Here's a tiny jsonp library to support this:

<script src="https://gist.github.com/1270230.js?file=jsonp-worker.coffee"></script>

So you can say:

<script src="https://gist.github.com/1270230.js?file=example.coffee"></script>