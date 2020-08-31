---
id: 1592
title: 'Doing It Right, You&#8217;re Doing It Wrong'
date: 2012-03-23T01:28:25+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1592
permalink: /doing-it-right-youre-doing-it-wrong/
categories:
  - SoftwareDev
---
Sometimes I will ask a question, say on StackOverflow and such-like, or maybe even IRL, and then be struck down as doing something wrong. The question's based on an evil assumption, so don't encourage him by answering it.

I get it, the importance of informing people The Right Way, especially if this question-asking friend of mine *cough* hadn't provided justification for the sly manoeuvre he or she is trying to pull off.

But there's a twilight zone between outright cowboyery and The Right Way. Fail fast! The code that's shipped is infinitely more useful to the world than the code that sits on your hard drive, irrespective of the respective quality levels. And with that in mind, there's a legitimate need for a theory of pragmatic programming practices. Practices which let you incur some technical debt while you get on with the job of launching an experiment and seeing if people find it useful. So instead of fashioning design patterns and guidelines around the best theoretical design, there should be more attention on ideas which explicitly let you cut a few corners, but cut the right corners!

*"Close a blind eye and this sh*t goes underground. That's when all hell breaks lose."*<br/>
- Hardened policy wonk in a movie which hasn't yet been made

A concrete example. In the more liberated languages, such as JavaScript and Ruby, there's decent object-oriented support, but it's not a requirement. You can still have global variables and functions sitting out there "in fresh air". And in Ruby, you can scope variables to a single file. For most big systems, The Right Way is indeed object-oriented for all the reasons OO is great. But for a system you're cobbling together organically, it's very possibly overkill. You risk analysis paralysis and end up writing extra infrastructure which may not be justified. On the other hand, globals everywhere may lead you down a dangerous path too early on. So there needs to be more of a science around finding the sweet spots in situations like this. Helping you walk the windy trajectory from Hello World to Bells And Whistles.

<iframe width="420" height="315" src="http://www.youtube.com/embed/FwaQxDkpcHY" frameborder="0" allowfullscreen></iframe>
[Cut Every Corner](http://simpsons.wikia.com/wiki/Cut_Every_Corner) as featured in [Simpsoncalifragilisticexpiala(Annoyed Grunt)cious](http://simpsons.wikia.com/wiki/Simpsoncalifragilisticexpiala(Annoyed_Grunt)cious)