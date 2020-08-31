---
id: 158
title: '&#8220;Hints on Programming Language Design&#8221; by C.A.R Hoare: Quick Summary'
date: 2005-07-09T21:16:21+00:00
author: admin
layout: post
guid: http://www.softwareas.com/hints-on-programming-language-design-by-car-hoare-quick-summary
permalink: /hints-on-programming-language-design-by-car-hoare-quick-summary/
dsq_thread_id:
  - "377025245"
  - "377025245"
categories:
  - SoftwareDev
---
[Hoare's "Hints on Programming Language Design"](http://www.iam.unibe.ch/~scg/Teaching/PS/PS-S05/Serie-1/Hoare_Hints.pdf) was written in December, 1973 and the first few pages on general principles are still very pertinent. Here's a summary.

* A programming language should support the three most difficult tasks in programming:
    * Program Design - "A good programming language should give assistance in expressing not only how the program is to run, but what it is intended to accomplish".
    * Programming Documentation: "A good programming language will encourage and assist the programmer **to write clear self-documenting code**, and even perhaps to develop and display a pleasant style of writing. **The readability of programs is immeasurably more important their writeability**.
    * Program Debugging: Various aspects of the language help reduce confusion, also compiler should be fast.

* Because programmers are reluctant to learn new languages, simplicity must be a priority if converts are to be gained. (Note: This is sad but true.)

* Principles:
 * Simplicity: "Some language designers have replaced the objective of simplicity by that of modularity". But what happens if a bug arises and the programmer doesn't fully understand what's going on? "Another replacement of simplicity as an objective has been orthogonality of design". e.g. complex numbers ... as with modularity, a good goal, but no substitute for simplicity.
 * Security: Shouldn't have to remove security features when going into production. **"What would we think of a sailing enthusiast who wears his lifejacket when training on dry land, but takes it off as soon as he goes to sea?"**. (Note: Good argument for run-time assertions.)
 * Fast Translation.
 * Efficient object code. Don't ignore performance and assume it can be optimised later on. (Note: are languages a reasonable exception to the optimise-on-the-fly school, or is this statement just obsolete?)
 * Readability: "In practice, experience shows that it is very unlikely that the output of a computer will ever be more readable than its input". (Note: Sad but true again. We're on the verge of [more powerful visualisations](http://www.softwareas.com/source-code-string-of-ascii-or-tree-of-goodness), but still not there 32 years after this paper was written.)

* On reflection (LISP-like programming etc): "The introduction of program structures into a language not only helps the programmer, but does not injure the efficiency of an implementation."