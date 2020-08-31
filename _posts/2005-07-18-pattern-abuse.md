---
id: 166
title: Pattern Abuse
date: 2005-07-18T23:17:18+00:00
author: admin
layout: post
guid: http://www.softwareas.com/pattern-abuse
permalink: /pattern-abuse/
dsq_thread_id:
  - "377039227"
  - "377039227"
categories:
  - SoftwareDev
---
Tony Darugar [hates patterns](http://www.parand.com/say/index.php/2005/07/18/i-hate-patterns/):

> Iâ€™ve seen more horrendous programming sins committed in the name of patterns than almost any other possible justification. 

I'm not sure if it's really worse than other justifications. "XP" and "agile", for example, are now being used to justify any (lack of) process not involving upfront design and documentation. That aside, pattern abuse is certainly a real phenomenon.

Patterns are just a form of expression. So saying "It's a good design because it uses Prototype" is like saying "It's a good article because it uses sarcasm".

Tony asks if it's the "patterns" themselves that are at fault, or the developer:

> Is this really a damnation of patterns or the case of a bad developer? My point is, this guy was not born a bad developer. He was quite smart, and couldâ€™ve been useful. There are many of this guy running around. Iâ€™ve seen them.

I don't know the guy in Tony's story, but I'd seriously question how good a developer he is, based on this story. **Anyone who thinks using a pattern is sufficient design rationale doesn't understand patterns or design or both.** Any design problem has infinite solutions and there are enough patterns in existence (even counting only the good ones) to justify many of those. So you'll need something more than "Hey everybody, I used a pattern!" to justify you've done a good job.

Patterns are great, but you don't "design by pattern". You learn patterns and you code with your own ability and you iterate between the two. 

To that end, I found test-driven design amazing when I first applied it, because the rapid code improvement loop meant patterns were just popping out. Only later did I realise how many patterns had just morphed their way into the code. The classes weren't *called* "Abstract Factory" and "Business Delegate". They just were. And, in many cases, I ended up with a far better understanding than I'd gained from just reading about them.

[Alistair Cockburn's](http://c2.com/cgi-bin/wiki?ShuHaRi)  [Shu-Ha-Ri analogy](http://alistair.cockburn.us/crystal/talks/wic/whatiscrystal090.ppt) analogy, taken from Aikido, is worth considering:
<pre>
What is expertise?  (the Shu-Ha-Ri progression)

      Level 1
      Learning â€œa technique that worksâ€
      Success is following the technique (and getting a success) 

      Level 2
      Learning limits of the technique
      Success is shifting from one technique to another 

      Level 3
      Fluid mastery - shifting techniques by moment
      Unable to describe the techniques involved
</pre>

No-one can get to Level 3 expertise on all the patterns and collections out there, but whatever level we're at, we can acknowledge that the mere application of a technique alone is not enough. Fortunately for martial arts students, they get to learn that lesson pretty quick.