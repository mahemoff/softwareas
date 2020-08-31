---
id: 1150
title: 'Mark Miller on Securing JavaScript: More Qcon Live Blogging'
date: 2011-03-11T19:40:00+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1150
permalink: /mark-miller-on-securing-javascript-more-qcon-live-blogging/
dsq_thread_id:
  - "375413832"
categories:
  - SoftwareDev
tags:
  - Conference
  - Javascript
  - QCon11
  - Security
---
Google Research's <a href="http://research.google.com/pubs/author35958.html">Mark Miller</a> is presenting a talk on Caja and web security. He emphasises that this is all bleeding-edge; no current browser fully supports this yet.

There are a ton of attack vectors for browsers, as shown on the Caja wiki. There are spec vulnerabilities, implementation vulnerabilities, and an ongoing arms race emerges. Mark shows a table of numerous variables for each browser, where the variation is not just wild but more or less random. The attacker only need to find one vulnerability here.

Perhaps the ongoing cat-and-mouse game means there's something wrong with the whole identity-centric paradigm. Instead, maybe we can look at access control - don't worry about who's sending the request, worry about if the request has the correct level of access.

Mark walks us through the history of web kludges - JSON and Comet for cross-domain calls and streaming, respectively. HTML5 gets us towards a truer web of distributed objects, which all leads towards a symmetric network.

<h3>Safe Mobile Messages: Uniform XHR</h3>

Uniform as in "Uniform Resource Location".

The proposal is for the server to ignore browser's "helpful" extras.

Authorise based on payload. HTTPS URL or request body - info the requestor knows.

HTML5 allows servers to waive response protection using "Access-Control-Allow-Origin: *".

<h3>Mobile Code</h3>

How do you mix coded from multiple untrusted sources into the same frame?

To solve this problem, we bring other security models to the world of JavaScript. With EcmaScript 3, Caja had to perform complex, server-side, translation with a runtime overhead.

The lessons of this effort were taken to the Ecmascript committee, and accordingly, EcmaScript 5 is one of the easiest OO languages to secure, instead of one of the hardest, as was the case previously.

<h3>Security as Extreme Modularity</h3>

This view treats security as an extreme form of modularity (ie the mutually suspicious components are seen as modules). Vulnerability is a form of dependency...so improving security also helps in other aspects, ie. makes the architecture cleaner.

So we marry up these closely related principles:
* Software Engineering Principle of info hiding: Need to know.
* Security Engineering Principle of least authority: Need to do.

These are the rules enforced:
* Memory safety and encapsulation
* Effects only by using held references
* No powerful references by default

Objects as Closures

[javascript]
function makeCounter() {
  var count=0;
  return {
    incr: function() { return ++count; }
    decr: function() { return --count; }
  };
}
[/javascript]

A record of closures hiding state is a fine representation of an object of methods hiding instance variables.

With "use strict", we can enforce freezing of values. So if you have object A which depends on object B, object A can freeze properties of object "B" to make sure the reference doesn't change. An important aspect of this is the ability to feeze a prototype.

For now, we have the "initSES.js" library. It monkey patches away bad non-standard behaviours, freezes whitelisted global variables...among other measures.

There's a concept of membranes (wrappers) to encapsulate/secure message passing. e.g. if you don't trust object X, you can make a read-only version of its return value. It's also possible to wipe out what's inside the membrane at some later stage, if desired. Even if that thing had references to external objects, only what was inside the membrane will be wiped.