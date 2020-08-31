---
id: 124
title: 'Software That&#8217;s Wrong and Knows It, Hungarian Notation'
date: 2005-05-12T18:15:34+00:00
author: admin
layout: post
guid: http://www.softwareas.com/124
permalink: /software-thats-wrong-and-knows-it-hungarian-notation/
dsq_thread_id:
  - "404421820"
  - "404421820"
categories:
  - SoftwareDev
---
**Minor Update (May 18, 2005): Hyphenated long variable name, it was causing havoc with Wordpress alignment.**

Joel Spolsky explains that [wrong code should be constrained to look wrong](http://joelonsoftware.com/articles/Wrong.html). I like this idea ... arrange things so that any evil code has a look of outright guilt. Joel focuses on naming conventions, but also lists several other worthy practices which serve to highlight wrong code:

<blockquote>
<li> Keep functions short.
</li><li> Declare your variables as close as possible to the place where you will use them.
</li><li> Donâ€™t use macros to create your own personal programming language.
</li><li> Donâ€™t use goto.
</li><li> Donâ€™t put closing braces more than one screen away from the matching opening brace.
</li></blockquote>

The part about naming is interesting, and provides another argument for [naming things carefully](http://programmasaurus.org): 
> The thing I want you to notice about the new convention is that now, if you make a mistake with an unsafe string, you can always see it on some single line of code, as long as the coding convention is adhered to

Hungarian notation, he explains, was meant to be about distinguishing between types in the high-level, semantic, sense, rather than types in the int-versus-float sense. True, but Hungarian is not the only way to do it. **High-level qualifiers should certainly be captured in variable names, but Hungarian prefixes are not the right way to go about it because they degrade readability**. Thankfully, conventions in Java and most other languages stay clear of prefixing variables with cute 2 or 3 character prefixes.

So, in Joel's example, "us" is the prefix for "unsafe" and s for "safe" (I'd probably call them "raw" and "escaped", but it's only an example and not the main point here). Personally, I'd rather see a variable called "unsafeAddress" than "uAddress". With the devoted Hungarian notation, it would probably be a lot worse too: "uszAddress" or something. **Code is a lot clearer when you can read the name  aloud, and it also improves communication among developers**. What are the objections to full qualifiers as opposed to abbreviations?

 * **"But you have to type more!"** You're still typing? That's, so, like, last week. With a completion feature in the IDE, you'll rarely if ever have to type anyway (Ctrl-Space in Idea, Ctrl-P in Vim, etc). Ed's your friend, get to know Ed, and all that.
 * **"But the code won't fit on one line!"** Really verbose names will push you over 80 columns, and that's best avoided. It could happen on occasion. Consider 2-column indenting, for starters - it actually looks better than it sounds. I'd advocate 120 or 160 characters anyway, given modern screen sizes and resolutions, but even with the quaint 80-column standard that was all the rage in the early 1900s, qualifiers won't push you over often.
 * **"But there will be a proliferation of prefixes!"** Nup. That will only happen if you're using prefixes for redundant details like variable type. If you're using it for sensible, high-level, concepts, you won't be bitten by an *uncompromisinglyResilient-NullableVariDiddlyaDoodlyableName*. (Long names can be useful as a transition thing, ideally only for a day or two until a clearly name emerges, at which point someone can digress for 7 seconds to hit Shift-F6 and enter a better name.)

Incidentally, one Hungarian-like convention I've occasionally seen in Java is capitalised statics. As in:

> Assertion.AssertTrue(cond);

I really like this convention. It provides a little bit of useful information without suffering from the main problems of Hungarian notation. It can still be read out loud as before, and adds no extra length to the name.<!--ee1a65a97f0eaf3f1bdeabdedd60b85d-->