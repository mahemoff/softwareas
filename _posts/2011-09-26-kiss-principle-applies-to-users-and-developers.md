---
id: 1368
title: 'KISS Principle Applies to Users *and* Developers'
date: 2011-09-26T10:40:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1368
permalink: /kiss-principle-applies-to-users-and-developers/
dsq_thread_id:
  - "426091441"
categories:
  - SoftwareDev
---
![](http://i.imgur.com/EKDFQ.jpg)

This week, Netflix re-branded its DVD-by-mail business into a separate division, "Qwikster". [The announcement](http://blog.netflix.com/2011/09/explanation-and-some-reflections.html) isn't too direct, but it's clear they see these as [different businesses]((http://www.bothsidesofthetable.com/2011/09/19/why-reed-hastings-should-be-applauded-for-netflix-split/)) with different constraints, there are different [licensing issues](http://www.wired.com/epicenter/2011/09/netflix-qwikster-split-licensing/) involved, and will probably spin off Qwikster at some point.

Keep It Simple, Stupid is certainly a vital way for large companies to ensure they continue innovating. I've seen this in more traditional industries. When everyone in sales fights nail and tooth to retain every weird component and configuration, you get short-term wins at the expense of long-term innovation.

But there's a challenge applying "KISS": **Keep It Simple, sure. But Simple for whom?**

**Qwikster keeps it simple for Netflix. Bully for you, Netflix. It doesn't keep it simple for the customer.** In fact, it makes it dramatically more complicated for the customer, doubling the number of places they need to manage movie queues  and payments. From a customer's perspective, Netflix was a place to keep a list of movies they want to see, regardless of the medium. If anything, it would make sense to *add* media, e.g. TV and cinemas.

So the simplicity of KISS is masking the important question of perspective. We need to separate "simple from user's perspective" from "simple from developer's (or company's) perspective":

![](http://picupper.com/2011/09/26/kissmatrix-9hx.png)

(where UX===User Experience and DX===#devexp===Developer Experience)

My own story is this. [WebWait](http://webwait.com) and [ListOfTweets](http://listoftweets.com) started life as a single file, and even when they went live, they were just static content. "Single Page Apps" with no server at all. That's wonderfully simple for me as the developer - I can develop on any computer without even setting up a server.

But this is KISS for the developer, not the user. The user is oblivious to the server's architecture, and they could receive precisely the same experience if the server was running PHP or anything else. In fact, the static-ness actually inhibited features, because it ruled out any server-side smarts. Specifically, server-less web apps can't store anything permanently (they can only use client-side storage) and can't communicate with the rest of the world (something which is less important thanks to JSONP and CORS, but still necessary for many applications).

At some point, I realised WebWait should capture snapshots, so I refactored the server to a Ruby Sinatra app, and added data persistence, which happily lets people link directly to a recording:

[blackbirdpie id="116743589337378816"]

A server with a database is more work for the developer, but still keeps things simple for the user, and because of the more complex framework, enables more useful features for the user. We could say the same about Netflix: If they'd been willing to deal with the extra complexity of the two business lines internally, they could continue to make things seamless for users.