---
id: 552
title: The Canonical Design Sketch
date: 2009-06-26T00:06:05+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=549
permalink: /the-canonical-design-sketch/
dsq_thread_id:
  - "377029269"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Architecture
  - CouchDB
  - diagrams
  - Software
---
We're having a TiddlyWeb fest tomorrow, and I explained one of the things I want to get out of it is a canonical design sketch.

Luke Hohman's superb text, <a href="http://www.amazon.com/exec/obidos/tg/detail/-/0201775948/">Beyond Software Architecture</a>, explains how he comes into a project and asks people to draw the architecture. A great predictor of the project's state is whether people come up with the same diagram. Put crudely, if they are all on the same page - if they all know module X is in the top-right and module Y is centre left - the project is onto a winner.

I've found similar things myself. I will work on a project for a while before someone puts up a poster depicting the emerging architecture. People will then find themselves congregating around the poster and building it up.

While some people are more visual than others, I believe most of us have good spatial abilities and a team has a lot to gain from a shared understanding of the architecture. This is even more so in the case of a framework like TiddlyWeb, where the community is disparate and connected much more loosely than a group of agile developers in a room together.

A good example of a design sketch is that by a project with some similarities to TiddlyWeb: <a href="http://couchdb.apache.org/">CouchDB</a>.

<img src="http://picupper.com/2009/06/25/couchdb.png" width="400px" />

I like the fact it's a sketch, not a boring old "formal" diagram. <a href="http://en.wikipedia.org/wiki/Notes_on_the_Synthesis_of_Form">Diagrams that are too neat are also brittle</a>, whereas simple sketches are resilient to change. Moreover, I like the fact it's on the homepage. That makes a bold statement to the community. This is the canonical design sketch for the project, and any discussions around architecture will naturally be couched around this sketch and the entities within.