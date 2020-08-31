---
id: 118
title: Self-Documenting is Self-Reinforcing
date: 2005-05-04T18:37:17+00:00
author: admin
layout: post
guid: http://www.softwareas.com/118
permalink: /self-documenting-is-self-reinforcing/
dsq_thread_id:
  - "375572198"
  - "375572198"
categories:
  - SoftwareDev
---
I just discovered [James Shore's blog](http://www.jamesshore.com). Lots of interesting stuff around agile development.
In particular, his post, ["Down With Comments"](http://www.jamesshore.com/Blog/DownWithComments.html). It refers to a recent slashdot article on comments in code: [Comments are More Important than Code](http://developers.slashdot.org/developers/05/04/26/2355242.shtml). As a guy who's keen on [self-documenting software](http://mahemoff.com/paper/software/SelfDocumentingSPA2005/selfdocumentingSpa2005.html), I have to say that's a rather provocative title.

Interesting, too, that many posters bought into the argument.

There are two sides to this debate, along with the obligatory hand-waving qualifications. In my experience, it often comes down to experience. As Alistair Cockburn has pointed out, methodologies are created due to fear, and fear comes from experiences. In the same way, **people who favour lots of comments have often worked with cruddy code and in reactive environments where there is no inclination to improve the situation. No wonder they fear raw code.** That most people have this experience should be evident from the fact that most environments, sadly, do actually work this way.

**As with many aspects of software development, there is a self-reinforcing feedback loop.** **In one universe, you can choose mediocre coding, not much refactoring, and lots of instructive comments.** Maintaining the instructions will take a lot of time up, so no further refactoring. With a shrug of the shoulders and a slightly guilty, "it's explained in the Javadoc", the instructions will be used to justify broken code. Self-propagating. **Meanwhile, in another universe, a conscious decision will have been made to strive for self-documenting code wherever possible. Some comments are justifiable, but they must earn their place: they are guilty until proven innocent, and can't just be slapped on to cover up fundamental coding flaws. In this universe, the code will benefit from well-considered terminology, consistency of conventions, architectural coherence. The process will support it too: tests will help alleviate the need for documentation while supporting refactoring, and the refactoring effort will be used to wipe out suspect comments. All code will be treated as living - developers will understand it, be on top of it, and, being humans, share the knowledge.** Alistair Cockburn comes to mind again: human conversation is much more effective than reading, and that includes reading comments.

HCI practitioners decided a long time ago that applications should work out of the box, because no-one reads instruction manuals anyway. People learn by doing and talking to others. Should software be any different?