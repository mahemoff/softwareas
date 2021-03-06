---
id: 94
title: 'The Generator Pattern for Unit Tests: Math.random() Takes a Beating'
date: 2005-04-13T21:15:27+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=94
permalink: /unit-testing-with-random-numbers-and-generators/
categories:
  - SoftwareDev
---
[Chris Stevenson](http://www.skizz.biz/archives/000568.html) discusses some pitfalls in testing with random numbers.

**Here's my advice on unit testing with random numbers: best avoid it and certainly don't tie yourself to it.** I'll explain the flexibility part below.
But First, let's be clear on randomness. As Chris alludes to, <b>random numbers in most programming environments are actually pseudo-random</b>. Math.random() says: " When this method is first called, it creates a single new pseudorandom-number generator". That's scary and confusing to many people, who assume random() means *random*. In fact, it's just a sequence of number generated by a formula. Like the digits of Pi, for instance. You can create a much more random sequence by taking inputs from the physical world, like current, mouse and keyboard movements, or [images of a lava lamp in motion](http://www.maa.org/mathland/mathtrek_5_7_01.html). But would you want to?

random(), then, is simply a sequence of numbers. I'd rather have a bit more flexibility on that sequence. So instead of:

<pre>
    nextInput = Math.random();
</pre>

I'd rather say:

<pre>
    nextInput = generator.generate()
</pre>

which implies some kind of Generator interface:
<pre>
     interface Generator {  // Not RocketScienceFolks
       Object generate()
    }
</pre>

Then, you can have any generation strategy you like. Math.random() becomes a special case. But, by wiring up the unit test with a different Generator implementation, you can have any sequence of numbers you care to name. More to the point, a single unit test can contain many tests which vary only on the generator. A generator like this can be configured with a pre-defined sequence of numbers, or use some strategy such as an arithmetic sequence. You then have more control and understanding over how you're systems being tested.

Here are four ways to generate test data:

* "Truly" random numbers - Not replicable. Might work on someone's desktop, then crash on a server. Painful. However, it does serve a purpose for some types of testing, such as stress and load testing. If you're abso-positive-ly sure you're systems working based on standard unit tests with replicable data, what's the harm in trying out completely random numbers before taking it live? If the code structure is in place, it's a cheap source of extra data to agitate your system with.

* Pseudo-random numbers - Can't see the use, unless it's just an implementation of a Generator, and even then, I'd generally prefer an understandable sequence. If I really want random to mess with the system, I'd rather use true random, because otherwise I'm just using the same numbers again and again, which defeats the purpose. (For those developers who make the mistake of performing all their unit tests with random  numbers, pseudo-random is at least a better approach due to replicability. Which leads to the happy double-negative that many people who actually want to random inadvertently use random() and are saved by the fact that random() isn't random.)

* Understandable sequence (such as an arithmetic or geometric sequence, modulo'd) - Very useful. I can reason about how long the cycle is before repetition take place, I can perform calculations on the sequence to determine expected answers. I know a lot more about what's going on than some obscure random() formula that's probably documented somewhere on the sun site. And in other languages, random() may well be unspecified and inconsistent across platforms. Also, let's say I'm using the sequence "2,4,6,8" and I see a "6" in the stack trace. Great, that tells me straightaway when the problem occurred. If I'd used a random sequence, I'd have to go and log all the values to fish out when the "6" occurred.

* Explicit sequence of literals (e.g. "1, 5, 6") - Also very useful. This is, of course, a generalisation of the standard unit-testing scenario ... specify an explicit input variable and verify the result. Sometimes, you just want to use a whole lot of numbers, which is where the sequence approach comes in handy.  So explicit literals works well in tandem with an automated sequence generator.<!--db6396ec4a8bc6f3e22b986245112824-->