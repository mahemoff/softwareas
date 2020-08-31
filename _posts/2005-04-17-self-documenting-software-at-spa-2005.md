---
id: 102
title: Self-Documenting Software at SPA 2005
date: 2005-04-17T16:23:10+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=102
permalink: /self-documenting-software-at-spa-2005/
categories:
  - SoftwareDev
---
OK, my final SPA posting. This time, some notes from my own workshop. In the next few days, I'll be doing a podcast (yes, I'm still officially podcasting after much silence!) on self-documenting software which will cover all this.

[The slides are online at my homepage.](a href="http://mahemoff.com/paper/software/SelfDocumentingSPA2005/selfdocumentingSpa2005.html").

**This was a 75-minute workshop to discuss practical techniques for achieving self-documenting software. I explained how usability principles can be applied to design and coding, we had a lot of interesting conversation and we performed some coding exercises.**

The workshop was interactive, with a couple of exercises. One was looking at a before-and-after code example, the other was a refactoring exercise. I'll post the code on the slides link above at some point. The conversation was good, people had a lot to say on the topic, so we didn't get as long on the refactoring exercise as I'd planned, but the trade-off was worth it. There's certainly a lot in this topic, an extended workshop is on the cards at some point.

* Since the workshop was entitled "Software, Document Thyself", I realised in retrospect some people might take this as an automatic document generation tool. So when I saw Cenqua's April 1 <a href="http://www.cenqua.com/commentator/">Commentator Tool</a>, I figured it was only fair to point those people in the right direction.

* Motivation for self-documenting software lasted all of about 60 seconds ... a quick survey indicated I would be preaching to the converted.

* I showed how we can draw from HCI theory to learn about coding techniques. **A well-worn assumption in HCI is that users don't read instruction manuals and shouldn't have to anyway, so design it to be as intuitive as possible. As Donald Norman explained, doors shouldn't need "Push"/"Pull" labels. So the design principles for self-documenting UIs have much to offer those of self-documenting code**, In particular:
    * Consistent Within an Application
    * Metaphor and Common Ontology
    * Consistent Across Applications â€“ Standard Ways to Accomplish a Task
    * Familiar Language
    * Attention Layering â€“ Overall Structure in a Blink

* I offered some specific points on: **reducing waste, providing affordances, refactoring, focusing on the typical case, learning trajectory - supporting the transition from novice to expert**.

* We discussed using a thesaurus and a little about my pet [Programmasaurus](http://programmasaurus.org) project. An exercise involved producing synonyms and discussing where we might use them. Some interesting comments here:

    * Where you use a term, as in many HCI concepts, depends on the context. You can't just say, use "get" here and "obtain" there.

    * There are often word pairings or groupings. For instance, some words don't have a clear opposite term.

* The refactoring exercise was interesting. I'd seeded a few spurious points which were quickly detected, but, moreover, there were various general ideas about how the refactorings might be accomplished. People were quick to point out Enums would help a lot with both examples. The Monty Hall example could have benefitted from enums to represent each door; the Connect 4 example from Enums to represent each side. With the Connect 4 example, there was some discussion about perhaps using java.awt.Color to encapsulate each side (red and green). Other points included elimination of useless setters/getters and renamings.

One group provided a nice demonstration of what is meant by service-oriented architecture (or inversion of control or pull principle, to use various other overloaded terms). They found one of the method names confusing, so the first thing they did was "Find Usages..." to understand its context and presumably help them rename it.