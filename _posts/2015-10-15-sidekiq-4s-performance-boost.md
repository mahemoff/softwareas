---
id: 2190
title: 'Sidekiq 4&#8217;s performance boost'
date: 2015-10-15T23:22:38+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2190
permalink: /sidekiq-4s-performance-boost/
categories:
  - Uncategorized
---
Mike Perham [managed to turbo-boost Sidekiq for v4](http://www.mikeperham.com/2015/10/14/optimizing-sidekiq/), making it six times faster. This in itself is good news for those of us who use it and his write-up is also of interest. #perfmatters

The perf tricks that made this possible:

1. Redis -> worker communication (dispatching new jobs to work on): Instead of a single, global, thread on the client taking requests from Redis and locally dispatching them, every worker now gets its own direct line to Redis.
2. Worker -> Redis communication (reporting when a job is complete): Instead of workers constantly updating the server, there's now a client-side proxy that updates it in batches every few seconds, ie it buffers up the pending updates and periodically sends them in a multiplexed message.
3. Refactored to do direct thread manipulation instead of relying on Celluloid.

Very interesting that (1) and (2) are almost the inverse of each other. Redis &rarr; worker job assignment has been switched from a global model to a per-worker model, while Worker &rarr; Redis job completion reporting has been switched from a per-worker model to a global model. So that's the time-honoured pendulum swing between centralisation and decentralisation, in a nutshell.

Also, as a commenter notes, it's not obvious how much has been gained by the withdrawal of Celluloid. Removing a library can not only increase complexity, but can be counter-productive to performance if the library captures years of performance boosts you'll otherwise have to learn yourself. Nevertheless, in the case of Celluloid, it was really there to simplify the multithreading programming effort, and given how important this is to Sidekiq, it's the kind of thing that often makes sense to take full control of. (The dubious refactorings are those where some peripheral feature like logging just had to be home-made. In the case of mission-critical functionality, there's often a lot to be said for DYI.)