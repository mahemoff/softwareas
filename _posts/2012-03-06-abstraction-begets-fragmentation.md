---
id: 1548
title: Abstraction Begets Fragmentation
date: 2012-03-06T09:50:11+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1548
permalink: /abstraction-begets-fragmentation/
categories:
  - SoftwareDev
tags:
  - Javascript
  - offline storage
---
Christian Heilmann raises [the ugly issue of offline storage](http://hacks.mozilla.org/2012/03/there-is-no-simple-solution-for-local-storage/). LocalStorage's synchronous nature makes it slow, WebSQL is deprecated, and IndexedDB's API induces headaches as well as being unsupported on many browsers. He asks whether the LocalStorage standard should be improved.

One of the predictable responses is "just use a wrapper library". We could use a fancy wrapper library that gives us the key-value simplicity of LocalStorage, but with an asynchronous API, and backed by those more beastly SQL-based solutions if they should exist on the device.

Now "a wrapper library" has all the usual concerns of abstractions. Does the common-denominator stance remove useful functionality from the underlying APIs? Does it separate the programmer so much from the bare metal that they can't get their head around performance issues? And so on. All true. But on the web, where open-source is so heavily used, wrapper libraries have an additional cost: Fragmentation.

So we end up with a dozen storage libraries on GitHub. BackStorage, SpineStorage, OrthopedicStorage, you name it. That's great, now we can use a nice API that works everywhere. Fast forward, and every programmer and their canine is writing offline single-page apps, so now we need libraries to cache, spool, and throttle messaging back to the server. Those libraries rely on underlying storage. Do they talk straight to the raw storage APIs? But then they'll spend all their time worrying about those APIs. So maybe they reuse one of those storage libraries. One of them uses BackStorage, another one uses SpineStorage, and a couple more use OrthopedicStorage. Yes, a whole plugin ecosystem gathers around each storage solution.

So which are you? Do you consider yourself a BackStorage man/woman? Card-carrying SpineStorage-head? Certified OrthopedicStorage practitioner? You'll need to pick one, because each is its own community with its own set of plugins and conferences. Not to mention the learning curve involved in adapting to something new. And the conflicts that arise if you try to use two wrappers in the same app. Wait, did SpineStorage.Login just stomp on that username I was trying to retain with BackStorage.Cache?

Choice is good and evolving faster than standards is good too. Which is why we do benefit enormously from wrapper libraries. But the cost of fragmentation is high. It can be justified if you're reaping the benefits of magic conferred by a highly opinionated framework. But if it's just there to cover up for a standard with an unnecessarily confusing API, I'd rather the browsers work on simplifying said API. Because I don't want to identify myself as a developer skilled in the arts of BackStorage/SpineStorage/OrthopedicStorage.

I'd rather just be a "web programmer".

<img src='http://i.imgur.com/J0wbW.jpg' />