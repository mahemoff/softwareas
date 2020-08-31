---
id: 115
title: Fancy Input in IDEs
date: 2005-05-03T02:00:51+00:00
author: admin
layout: post
guid: http://www.softwareas.com/fancy-input-in-ides
permalink: /fancy-input-in-ides/
dsq_thread_id:
  - "389688889"
  - "389688889"
categories:
  - HumansAndTech
---
There's been a lot of talk about viewing code in fancy ways. For instance,  [James Gosling's work on Jackpot](http://www.softwareas.com/source-code-string-of-ascii-or-tree-of-goodness).

Well, how about fancy input as well?

Some ideas from the world of HCI:

* **Speech input:** Speech is a great way to switch modes and perform simple tasks, without lifting your hands off the keyboard and without moving the mouse back and forth. I would respect an IDE that let me **utter such commands as "Build" and "Test", and such mode switches as "Debugger" and "SampleInput.xml"**. This isn't intelligent human-robot relations; just simple commands to stupid routines. Easy enough in 2005, even with background noise and diverse accents.

* **Drag-and-drop:** Since the source is now a structured object for the purposes of refactoring and syntax highlighting, let me manipulate it as such. Much as a Lisp program might do. For instance, **I should be able to drag a class from the package view into a source file, which would create a new instance variable.** Or I could pick up a method in the source file and drag it into another class in the package view.

* **Source-Based Refactoring:** We already have the lightbulb-based "intents", which suggest code changes based on the current state. However, that's only based on the static state of the code: the sequence of characters as it currently stands. How about looking at what the programmer's actually doing. Oh-oh, this is getting into "Hi I'm Annoying, you seem to be writing a letter. Would you like me to 'help' you?". Well, just because an idea was poorly executed doesn't mean it can't work. For instance, **you should be able to perform a "Change Signature" refactoring by ... changing the signature! Directly. Not by opening up a "Change Signature" dialog box, which involves a distracting jump to a new level of abstraction and a completely different interaction paradigm. But by simply moving some text around.** If the IDE detects you've done that, it could automatically - oh, and unintrusively - suggest a Change Signature refactoring.  Most refactorings I can think of could be detected by watching the user change the source directly. Deleting text or pulling a member up, for instance. You could extract a method by selecting the entire code block and then replacing it by simply typing the method name.

These thoughts are only based on novel input with today's technology. It will get a lot better than that as we learn about how future rendering algorithms best interact with future input mechanisms.