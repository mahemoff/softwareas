---
id: 409
title: 'Designing Like a Pollyanna: Have your Cake and Eat it Too'
date: 2007-11-23T03:34:22+00:00
author: admin
layout: post
guid: http://www.softwareas.com/designing-like-a-pollyanna-have-your-cake-and-eat-it-too
permalink: /designing-like-a-pollyanna-have-your-cake-and-eat-it-too/
dsq_thread_id:
  - "375573440"
categories:
  - SoftwareDev
tags:
  - Design
  - Patterns
---
<blockquote>"The novel's success brought the term "pollyanna" (along with the adjective "pollyannaish" and the noun "Pollyannaism") into the language to describe someone who is cheerfully optimistic and who always maintains a generous attitude toward the motives of other people. It also became, by extension â€“ and contrary to the spirit of the book â€“ a derogatory term for a naÃ¯ve optimist who always expects people to act decently, despite strong evidence to the contrary."</blockquote>

<a href="http://en.wikipedia.org/wiki/Pollyanna">-- Wikipedia entry for <i>Pollyanna</i></a>

A little while ago, I was talking to some colleagues about an authentication problem. I suggested we need to improve its usability and my colleague's immediate response was to argue there's a security-usability trade-off, i.e. by improving usability, we must resign ourselves to decreasing security. Push one lever down, the other goes up. I've never bought into this argument. While certain forces do often conflict with each other, they don't always, and it's counter-productive to constrain your solution space with immediate presumptions like that.

Clarke Ching triggered this post with his posts on <a href="http://www.clarkeching.com/2007/10/non-zero-sumnes.html">Non-Zero Sumness</a> and <a href="http://www.clarkeching.com/2007/10/cake.html">having your cake and eating it</a>. The latter is an example of a twerpy category of fallacious sayings and assumptions in this world which are based on scarcity mentality. For example, the notion that you have to "divide the pie" so that a gain for A is a loss for B. The alternative (as a certain presidential candidate was ridiculed for pointing out) is to make the pie higher. Whoever invented multi-storey buildings figured this out a long time ago. 

(BTW <a href="http://en.wikipedia.org/wiki/Have_one's_cake_and_eat_it_too">"You can't have your cake and eat it too"</a> is a ridulous premise; what else are you supposed to do with your cake? I see from the wikipedia article that the original phrasing "wolde you bothe eate your cake, and have your cake?" is the reverse and makes more sense - you can't eat your cake and still have it.)

Fortunately, we have sayings and phrases which remind us that it doesn't have to be a trade-off. Unfortunately, these terms have been over-used by the proverbial "MBA suit guy" that we're not allowed to use them without offering an apology. e.g. "win-win" and "synergy". (Both terms I use without apology. I will stop short of "gestalt" though.)

All the above is theoretical rambling - here are some real-world examples.

<ul>
<li><b>Security-Usability</b> Biometric authentication allows people to enter places without typing a password or carrying a card, and is, generally (and theoretically) speaking a more accurate indication of a person's identity. Neither security nor usability suffers from this technology; both have been enhanced. (Privacy advocates will argue there is still a trade-off at stake.)
<li><b>Safety-Usability</b> As with security, safety is often assumed to be at odds with usability. In our work on <a href="http://mahemoff.com/paper/safetyscs/">safety-usability patterns</a>, we sought synergies which would ideally improve both at the same time. For example, the pattern called "Behaviour Constraint", sometimes referred to as a "forcing function". In some buildings, when there's a fire, a barrier goes up on the stairs leading to the basement, to ensure people don't keep running down there (example by Don Norman). The wheels of a plane can't be raised if the plane isn't moving (to prevent a pilot from actually raising them while on the tarmac). These are examples which make life easier for users, by reducing the number of decisions they have to make, and at the same time, improve safety by blocking the transition to dangerous states.
<li><b>Ajax-Accessibility</b> When Ajax emerged, some people had a knee-jerk response - "Ooooh! Javascript! Bad for accessibility!". In some cases, it was true. In many other cases, though, Ajax actually improves accessibility. e.g. Ajax makes it much easier to let people choose font size and colour scheme.
</ul>

Knowing that certain forces trade off against each other is still useful as a kind of broad-brush stereotype. At a meta level, it's a kind of general software engineering pattern to say "security and usability trade off against each other". (It's a pattern in the sense that if you looked at hundreds of software projects, you'd see people frequently dealing with this trade-off.) I would like to explain such a pattern to a first-year software engineering student, so they can more easily reason about how these things work. It's also useful in scrutinising a design; I would be quite comfortable ending up with a design with "high" security and "low" usability, or vice-versa, after exploring all the options, because I know these principles do usually trade off. And for that reason, I'd consider it somewhat unrealistic for a client to expect a feature to have both "high" security and "high" usability, and would only engage on such a quest after explaining to said client that the effort has a high chance of failing to meet these criteria.

So these trade-offs are useful and are my defence against the second part of the Pollyanna definition above - "a derogatory term for a naÃ¯ve optimist who always expects people to act decently, despite strong evidence to the contrary." I'm not ignoring those trade-offs, I'm just saying they shouldn't be an automatic assumption. It plays to a higher-level rule about design and creativity: Ignore constraints at first. In too many cases, people are afraid of going down certain paths because they can immediately detect an obstacle down the road. I once tried producing a novel design with a domain specialist who would immediately shoot down most any idea I had on the basis that users would never work with it. Once I bypassed him and got to the users themselves, the situation was quite different; the users embraced the concept and gave further suggestions for improvement. The domain specialist, who had long since working as an active user, was applying constraints too early and preventing us from proving the concept (<a href="http://www.softwareas.com/proving-a-technology">"proving" == "bashing into shape"</a>). In many other cases, the barrier is technical - you come up with an idea and it's immediately blocked on the basis that it can't be done with current technology. (The sort of limiting belief you would have heard if you proposed Google Maps in 2004). In the same way, when we automatically assume "improving X will diminish Y", what we're doing is limiting our options prematurely. Better to ask first "is there a way I can improve both", or, failing that, "is there a way I can deliver the critical attribute X without diminishing Y too much?".