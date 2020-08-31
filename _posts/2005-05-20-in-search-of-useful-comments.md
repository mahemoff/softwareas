---
id: 130
title: In Search of Useful Code Comments
date: 2005-05-20T18:02:41+00:00
author: admin
layout: post
guid: http://www.softwareas.com/in-search-of-useful-comments
permalink: /in-search-of-useful-comments/
dsq_thread_id:
  - "400093114"
  - "400093114"
categories:
  - SoftwareDev
---
Couple weeks ago, I argued that [self-documenting code is self-reinforcing](http://www.softwareas.com/self-documenting-is-self-reinforcing). [Some choice quotes on this topic from Mike Clarke](http://www.stickyminds.com/testing.asp?Function=edetail&ObjectType=ART&ObjectId=9041&tth=DYN&tt=siteemail&iDyn=3)  (via [his blog](http://www.clarkware.com/cgi/blosxom/2005/05/19#CCComments)) (emphasis mine):

<blockquote>
Ever since I was a wee programmer, I've been reminded that good code has a lot of comments ... <b>The trouble is, I can't ever remember being taught this important lesson: Learning to remove a comment can lead to improvements in the code</b> ... It turns out that good code actually needs fewer comments than does bad code.
</blockquote>

He goes on to suggest **when comments smell sweet.** Here's my thoughts on these (which essentially amounts to some "me too" gushing):

* Class purpose

I too think this is usually worthwhile, although by no means should it be necessary for all classes.

* Gotchas, assumptions, limitations, explanations for decisions that aren't obvious

There's definitely a place for this stuff, and the aim of self-documenting shouldn't lead to people feeling bad about commenting on this stuff. Again, it's interesting that this is actually the most useful type of comment to have, but many people don't like including it because it seems wrong to have a comment like "this is confusing, but we're still waiting on an answer from the client". That's the same kind of thinking that vendor-written manuals often adopt - even though the product is faulty, they'll ignore any problems and make users feel bad that they can't work things out.

* TODOs and problems in the code

As with the gotchas, it's worth having this, and it's much better when it's in the code and you can read, update, and search for it.

* Use of a published algorithm

And, likewise, pointers to patterns. That's the power of patterns: mention a couple of names and you can get a quick boost in understandability. to be sure, it can still be reduced by careful design: there's no need to say you used the Proxy pattern if you're class is called "CalculatorProxy", and there's no need to say you used Factory Method if your Car class is "Car createFastCar()".