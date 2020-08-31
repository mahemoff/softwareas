---
id: 231
title: 'HTTP Streaming: An Alternative to Polling the Server'
date: 2005-11-04T06:11:29+00:00
author: admin
layout: post
guid: http://www.softwareas.com/http-streaming-an-alternative-to-polling-the-server
permalink: /http-streaming-an-alternative-to-polling-the-server/
dsq_thread_id:
  - "375436421"
  - "375436421"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Firefox
  - HTTP
  - IE
  - Javascript
  - JotLive
  - Links
  - Nevow
  - Streaming
  - XMLHttpRequest
---
**If Ajax apps are to be rich, there must be a way for the server to pass new information to the browser. For example, new stock quotes or an instant message someone else just sent you. But the browser's *not* a server, so the server can't initiate an HTTP connection to alert the browser. The standard way to deal with this dilemma is [Periodic Refresh](http://ajaxpatterns.org), i.e. having the browser poll the server every few seconds. But that's not the only solution.**

The [recent podcast on Web Remoting](http://www.softwareas.com/ajax-basics-podcast-2) includes a discussion of the **[HTTP Streaming](http://ajaxpatterns.org/HTTP_Streaming) pattern. By continuing to stream information from the server, without closing the connection, you can keep the browser content fresh.** I wasn't aware that it was being used much on the public web, since it can be costly, but I recently discovered [JotLive](http://jotlive.com) (which is only semi-public since it requires registration) is indeed using it. Do you know any other examples?

[Ajaxian.com's interview with Abe Fettig of JotLive](http://www.ajaxian.com/archives/2005/09/jotspot_live_li.html):

> How do you handle the "live" part? Polling?

> We're using a (very slightly modified) version of LivePage, which Donovan Preston wrote as part of Nevow, a Python library for building web applications using the Twisted networking framework (which I just wrote a book on: Twisted Network Programming Essentials). LivePage doesn't use polling. Instead, it uses a clever technique where each browser keeps an open XMLHTTP request to the server at all times, opening a new connection each time the old one closes. That way every client viewing the page is constantly waiting for a response from the server. When the server wants to send a message to a client, it uses the currently open request. So there's no waiting.

A few (edited) extracts from [the HTTP Streaming pattern](http://ajaxpatterns.org/HTTP_Streaming):

**Alternative Pattern:** [Periodic Refresh](http://ajaxpatterns.org/Periodic_Refresh) is an obvious alternative to HTTP Streaming. It fakes a long-lived connection by frequently polling the server. Generally, **Periodic Refresh is more scaleable and easier to implement in a portable, robust, manner. However, HTTP Streaming can deliver more timely data, so consider it for systems, such as intranets, where there are less simultaneous users, you have some control over the infrastructure, and each connection carries a relatively high value.**

**Refactoring Illustration:** The [Basic Wiki Demo](http://ajaxify.com/run/wiki), which uses Periodic Refresh, has been refactored to use [http://ajaxify.com/run/wiki/streaming](HTTP Streaming).

**Solution:** <br />
**Stream server data in the response of a long-lived HTTP connection.** Most web services do some processing, send back a response, and immediately exit. But in this pattern, they keep the connection open by running a long loop. The server script uses event registration or some other technique to detect any state changes. As soon as a state change occurs, it pushes new data to the outgoing stream and flushes it, but doesn't actually close it. Meanwhile, the browser must ensure the user-interface reflects the new data. This pattern discusses a couple of techniques for Streaming HTTP, which I refer to as "Page Streaming" and "Service Streaming".
<br />
**"Page Streaming" involves streaming the original page response. Here, the server immediately outputs an initial page and flushes the stream, but keeps it open. It then proceeds to alter it over time by outputting embedded scripts that manipulate the DOM. The browser's still officially writing the initial page out, so when it encounters a complete &lt;script&gt; tag, it will execute the script immediately.** A simple demo is available at [http://ajaxify.com/run/streaming/](http://ajaxify.com/run/streaming/).
<br />
...(illustration and problems)...
<br />
**"Service Streaming" is a step towards solving these problems, though it doesn't work on all browsers. The technique relies on XMLHttpRequest Call (or a similar remoting technology like IFrame_Call). This time, it's an XMLHttpRequest connection that's long-lived, instead of the initial page load.** There's more flexibility regarding length and frequency of connections. You could load the page normally, then start streaming for thirty seconds when the user clicks a button. Or you could start streaming once the page is loaded, and keep resetting the connection every thirty seconds. Having a range of options helps immeasurably, given that HTTP Streaming is constrained by the capabilities of the server, the browsers, and the network.
<br />
...
<br />
Experiments suggest that the Page Streaming technique does work on both IE and Firefox ([1]), but Service Streaming only works on Firefox, whether XMLHTTPRequest ([2]) or IFrame ([3]) is used. In both cases, IE suppresses the response until its complete. You could claim that's either a bug or a feature; but either way, it works against HTTP Streaming.
<br />
...
<br />
Donovan Preston explains the technique he uses in [Nevow](http://nevow.com/), which overcomes this problem:
<br />
> When the main page loads, an XHR (XMLHttpRequest) makes an "output conduit" request. If the server has collected any events between the main page rendering and the output conduit request rendering, it sends them immediately. If it has not, it waits until an event arrives and sends it over the output conduit. Any event from the server to the client causes the server to close the output conduit request. Any time the server closes the output conduit request, the client immediately reopens a new one. If the server hasn't received an event for the client in 30 seconds, it sends a noop (the javascript "null") and closes the request.