---
id: 213
title: 'New Patterns: XMLHttpRequest Call and IFrame Call'
date: 2005-10-10T01:29:08+00:00
author: admin
layout: post
guid: http://www.softwareas.com/new-patterns-xmlhttprequest-call-and-iframe-call
permalink: /new-patterns-xmlhttprequest-call-and-iframe-call/
dsq_thread_id:
  - "376011509"
  - "376011509"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - IFrame
  - Javascript
  - Links
  - Patterns
  - Remoting
  - Software
  - Web
  - Web2.0
  - XMLHttpRequest
---
Full drafts are now online for the two big Web Remoting patterns: <a href="http://ajaxpatterns.org/XMLHttpRequest_Call">XMLHttpRequest Call</a> and <a href="IFrame_Call">IFrame Call</a>. There are also a couple of new demos to illustrate GETting and POSTing with both call types: <a href="http://ajaxify.com/run/xmlHtttpRequestCall/">XMLHttpRequest Example</a>, <a href="http://ajaxify.com/run/iframe">IFrame Example</a>.

A few extracts follow, but first, let me ask you: **Do you know of any public IFrame remoting examples?** Google Maps is the only public example I know. All the other examples here are tutorials and framework demos.

The XMLHttpRequest alternatives was the most fun thing here (headings shown below). I went through the various techniques I've seen, read about, and tried out, to list as many ways as possible to programmatically call the server. As you might expect for these "Foundational Technology" patterns, there's a lot more code in the Solutions than in later patterns, where the focus shifts more towards the -ilities, particularly usability and maintainability.

**As usual, feedback much appreciated.** (Mainly on the content, rather than woeful spelling and outright grammatical disasters at this stage.)

<h3>XMLHttpRequest Call</h3>

**Solution:**
**Use XMLHttpRequest objects for browser-server communication.** XMLHttpRequest is a Javascript class capable of calling the server and capturing its response. Just like a browser or a command-line web client, an XMLHttpRequest issues standard HTTP requests and grabs responses. Note: The code shown throughout this demo is closely based on an online companion demo (http://ajaxify.com/run/xmlHttpRequestCall/).

<example omitted.>

The above example hopefully illustrates that the fundamental technology is pretty simple. However, be aware that it's a very basic usage, not yet fit for production. Fundamental questions remain:

    * How can XMLHttpRequests be created?
    * How does an asynchronous call work?
    * How do our code detect errors?
    * What if the service requires a "POST" or "PUT" request rather than a "GET"?
    * Which URLs can be accessed?
    * How can you deal with XML responses?
    * What's the API? 

The following sections address these questions and show how the code above needs to be modified. 
...

**Decisions**
<pre>
6.1 What kind of content will web services provide?
6.2 How will caching be controlled?
6.3 How will you deal with errors?
</pre>

**Alternatives:**
<pre>
9.1 IFrame Call
9.2 Persistent Connection
9.3 Richer Plugin
9.4 On-Demand Javascript
9.5 Import XML Document
9.6 Image-Cookie Call
9.7 Stylesheet Call
</pre>

<h3>IFrame Call</h3>

**Solution:**
**Use IFrames for browser-server communication.** IFrames are page-like elements that can be embedded in other pages. They have their own source URL, distinct from their parent page, and it can change dynamically. IFrame Calls work by making the IFrame point to a URL we're interested in, then reading the IFrame's contents once the new content has loaded.
</example>