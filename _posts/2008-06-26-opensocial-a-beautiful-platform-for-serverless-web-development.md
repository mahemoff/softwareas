---
id: 456
title: 'OpenSocial: A Beautiful Platform for Server-less Web Development'
date: 2008-06-26T20:46:42+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=453
permalink: /opensocial-a-beautiful-platform-for-serverless-web-development/
dsq_thread_id:
  - "377061168"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Ajax Patterns
  - Cloud
  - Gadgets
  - OpenSocial
  - Programming
  - Web
  - Web 2.0
---
<img src="http://picupper.com/2008/06/26/heartopensocial.png" />

It's belatedly dawned on me how OpenSocial makes a great server-less Ajax platform. When you create an OpenSocial gadget, you're building a lil Ajax app that performs much coolness that would normally require a server, but doesn't. Effectively, you're delegating the duties of the gadget's host environment. All you have to do is write a single XML file and host it somewhere. In fact <a href="http://code.google.com/apis/gadgets/docs/legacy/gs.html#Scratchpad">Google Gadget Editor</a> gives you an editor to write it in and a place to host it.

In fact, this is so good that if I was teaching someone Ajax in 60 minutes or less, I would consider getting them to write a gadget. It's that simple. Previously, I might have got them to write a static HTML file, with embedded Javascript and CSS, but now they can do the same thing <em>and</em> benefit from server-side features too, features they never had to install. This is like getting the usual benefits of the DOM and the Javascript API, but with much more.  You're getting both a set of APIs, just like when you use JQuery or Prototype, but you're also getting a server which many of those APIs rely on. So it's a true platform.

By the way, I'm assuming you're using XML content type, not URL. XML content type is the way forward, especially as we move to <a href="http://code.google.com/p/google-caja/">a Caja world</a>. XML gadgets will get you the richest functionality. URL gadgets are only suitable for legacy concerns, and in some cases, accessibility.

So you're using XML content type, which means the entirety of your Ajax app lives in one file. What does an OpenSocial platform provide to your little XML gadget spec?

<ul>
  <li><strong>Persistence.</strong> The most important thing is you can save application data. You can serialise any state you care to persist, and then store it as a hidden user preference. This is really neat. It means you can write a TODO gadget, for example, and ensure all the TODO tasks will be saved, but without having to store them on your own database and without having to build a persistence layer around it. And of course, the platform will (theoretically) provide the necessary security to ensure users only see their own tasks.</li>
  <li><strong>Preferences.</strong> You can easily let users customise your app via the preference API. For free, you get form fields to let users state their preferences, with drop-downs for enumerated types. And of course, the preferences are persisted without any effort on your part.</li>
  <li><strong>Content Fetching.</strong> It gets even better. <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a> is often bigged up as the way to get data from third parties. But thanks to OpenSocial's remote fetching APIs, it's just as easy to grab content via the containers <a href="http://ajaxpatterns.org/Cross-Domain_Proxy">Cross-Domain Proxy</a>. This means you can get any internet content and call any API, not just those specifically designed for cross-domain browser calls. There are also value-adds here, e.g. caching, scheduling periodic updates, converting feed data of any format into a consistent JSON structure.</li>
  <li><strong>Identity and Social Networking.</strong> Ah yes, the almighty "social" in OpenSocial. On the right platform, your server-less Ajax app can get info about the page owner and the page viewer, and their friends. Friends and social stuff and knowing whose page it is, that's cool and all. But what's really exciting here is much simpler than that - it's simply IDENTITY. What matters most is: With a single API call, you get an ID for the guy viewing your gadget!!! You didn't have to handle registration, password reminder links, etc. etc., and go through all the associated security questions around it. All the usual stuff you have to do if you want to know who's using your application. It's all *free* to you, gadget developer. (Downside is your company doesn't "own the user", so your gadget will never get you pina coladas on the beach at noon and an environmentally-conscious hybrid vehicle to sip frappachino grand&egrave;s in.) With this user handle, you can also save a hashmap of information about the user, persisted by our friend the server.</li>
  <li><strong>Many other services.</strong> Each platform is free to provide any number of features beyond the required API; this is how platforms compete against each other in the OpenSocial world. "Feature" is actually the term used for a particular set of browser and server services, e.g. "dynamic height" - the ability for a gadget to update its height - is a standard OpenSocial feature. Notifications - the ability for gadgets to add little notes to the top which the user must manually clear - well, that's a custom feature iGoogle provides but others don't. So anyway, there are lots of these features and your gadgets get them for free. In most cases, they are just libraries which you could also get for free by using Scriptaculous or whatever...but still, with OpenSocial, it's really, really, easy! No download or installation. (Although it must be said that with library CDNs like Google's new effort, you can also use many Ajax libraries without installation too. The difference here is that at least some of these features are tied to server-side services as well.)</li>
</ul>

So, these days, OpenSocial may well be the easiest way for a newbie to learn Ajax, and for any developer to get an Ajax app up and running. I actually think we need more tools and services to allow standard Ajax apps - not gadgets - to get up and running fast too. After all, the UI in OpenSocial is based on a widget/gadget model, and this is a mini web app running on a bigger page. Nowadays, we have canvas gadgets, which are bigger, but still not so big and run inside another web page. What if you took the same cloudish platform principles and applied it to a big old Ajax app, occupying the entire page and with its own URL (though probably coming from the platform's domain). You can sort of do that already by looking at the content of the gadget iframe, but it's not designed for that purpose...and if it was, you could do some interesting stuff.

For instance, I envisage a simple-to-use cloud storage system based around principles of Persevere and CouchDB, and for limited use, it could even allow anonymous access. I'll perhaps demo all this at some stage.