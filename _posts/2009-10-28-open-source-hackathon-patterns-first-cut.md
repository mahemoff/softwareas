---
id: 680
title: 'Open-Source Hackathon Patterns: First Cut'
date: 2009-10-28T00:24:31+00:00
author: admin
layout: post
guid: http://softwareas.com/open-source-hackathon-patterns-first-cut
permalink: /open-source-hackathon-patterns-first-cut/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574494"
categories:
  - SoftwareDev
---
This is my first cut at identifying process/organisational patterns
we've used and evolved for running hackathons at Osmosoft. Many are
regular agile patterns, specialised for the Osmosoft-style hackathon
context.

I described <a href="http://softwareas.com/wikidata-hackathon-wikidata-a-wiki-of-companies-data">one
particular hackathon</a> in detail a few months ago. We've done about
half a dozen of them now,for a range of different customers, with
requisite navel-gazing in between the events, so we have begun to get
an idea of what works and what doesn't. Hopefully, these patterns will
help to broaden the conversation and help us further evolve our
practices.

<h3>Preparation Patterns</h3>

* Skeleton Project - A live skeleton project is prepared before the event.
* Functional Plugin - Certain generic plugins required for the hackathon should be identified and built, if time permits.
* User Stories - Team and customers agree on user stories, with priorities.
* Fixed Duration - Team and customers agree upfront on finishing time.
* Customer Agreement - Customers agree on their obligations and expectations.

<h3>Development Patterns</h3>

* Open-Source Code - The hackathon develops open-source code, to be placed in a public repository throughout the day (proprietary features can be integrated via plugins and configuration at a later date).
* Continuous Integration - Everyone checks into the central repo and builds/tests on their local machine.
* Public Instance - An instance, continuously built from the repository, is available to the customer (speculative).
* Dedicated Integrator - One developer supports code integration and continuous integration, instead of developing to user stories.
* Customer Liason - One developer is primarily responsible for engaging with customers before, during, and after the hackathon.
* Stand-Up Meetings - Periodic stand-up meetings throughout the day, with each meeting deciding the time for the next meeting.

<h3>Post-Development Patterns</h3>

* Walkthrough - Developers walk through final product
Screencast - Final product is captured as a screencast, to be published online.