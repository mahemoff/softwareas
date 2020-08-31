---
id: 444
title: Models of Open Source
date: 2008-05-06T07:38:09+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=441
permalink: /models-of-open-source/
dsq_thread_id:
  - "375573691"
categories:
  - SoftwareDev
tags:
  - GNU
  - MIT license
  - open source
---
<img src="http://picupper.com/2008/05/05/DilbertOnOpenSource-59z.gif" />

Controversy arose in several open source projects last week: Ext JS, SpringSource App Platform, and the SWF/FLV specs. <a href="http://almaer.com/blog/being-open-is-hard-as-we-have-seen-this-week">Dion has a good summary</a> and concludes with a reminder that most people could care less:

<blockquote>
Finally, I know that 99% of the developers out there may not even care, let alone users. There are open source wonks who like to argue about licensing and methodologies. As I watched the John Adams HBO series, I felt a little like those fine chaps arguing over the finer details of things. Many of the people didnâ€™t know what was going on there, or why a particular Article was written the way it was. But, they had drastic implications for the people. I think that the same can hold here for some of the projects.
</blockquote>

Now this ignorance of open source models in my experience and an interesting phenomenon. It took open source until around the middle of this decade for even the basic definition of open source to be understood, and to some extent, accepted, by mainstream IT and business communities. That's about five decades after the practice began, two decades after <a href="http://en.wikipedia.org/wiki/GNU_Manifesto">Stallman's GNU Manifest</a>, and almost a decade after Raymond et al declared "Open Source" teh nu k00lness.

The basic definition of open source is understood, but as Dion notes, most people have no idea how the models vary, or what the implications are. Which is unfortunate, because the commercial implications are indeed vast.

<img src="http://picupper.com/2008/05/05/cover-qyx.jpg" />

I consider myself an expert on this topic ;P because I once picked up a copy of an <a href="http://safari.oreilly.com/0596005814">O'Reilly book on open source models</a> at a heavily reduced price and flicked through it intensely for at least two hours. Okay, so not quite an expert (!), more an armchair ignoramus, but certainly a stakeholder as both a consumer and publisher of open-source. And I'm hardly the Richard Stallman of the Ajax world either, but whenever I publish software that could potentially be used or adapted by someone, I make the tiny effort of including a license notice. Sometimes it almost seems arrogant to do so when the software is so trivial, but I'd rather do that than leave the license unstated, in which case it would come under the silly default, i.e. standard restrictive copyright. (Even if you agree with standard copyright, doesn't it seem silly that rights to anything anyone creates belongs to them by default, and for the greater part of a century?) 

Well, since I include a notice, I've had to think about which license to use.

In my dim-witted view of models, there are three key categories. All allow people to use it free of charge and generally remove any liability from the provider. They vary in what happens when people change it:

* <a href="http://en.wikipedia.org/wiki/Copyleft">Copyleft/Viral</a> (e.g. GPL, Creative Commons Share-Alike) - Anyone who modifies it must release the modified version.
* <a href="http://en.wikipedia.org/wiki/Permissive_free_software_licences">Permissive</a> (e.g. MIT,  BSD, Apache) - You don't have to release your modifications, though you still have some restrictions such as retaining the original license and author details.
* <a href="http://en.wikipedia.org/wiki/Public_domain">Public Domain</a> - Anything goes.

There are other distinctions too, e.g. around charging and attribution to the original creation; but the above distinction is the most important in most cases. And this is the sad thing: most IT and business people simply don't understand these distinctions and the implications they have.

You can argue about ethics until you're blue in the face, but the reality is, there's no absolutely "right" or "wrong" model. It's just horses for courses and being aware of the implications. Personally, I do have a hard time justifying copyleft-style licenses and I sometimes wonder how many people release stuff as GNU just because they associate it with open-source, without realising the full implications. I've worked in many commercial situations where GPL is unacceptable and I hate the idea that developers will be in the same situation as me, i.e. gleefully eyeing something that would scratch their itch, but not being able to use it. Incidentally, Ajax Patterns was initially released with the more permissive Creative Commons license, but following the book deal, O'Reilly asked me to change it to share-alike as it discourages other publishers from publishing their own version of the same book, which has apparently happened in the past. This is similar to the reason some companies release dual  licenses - GPL and standard copyright. It means anyone can use it for free under GPL, but other companies can't update and re-distribute for a fee. I can see that. It creates an incentive to release as open-source.

It's convenient for me to have a default license choice, so I don't have to think too hard whenever I release something. I have chosen <a href="http://en.wikipedia.org/wiki/MIT_License">The MIT License</a> because it is extremely concise, and is basically the smallest (in words) mainstream license that satisfies my main aims: To allow people to work with it freely and free of the restrictive burden GNU creates; to receive credit for my work; to be free of liability. The three paragraph license can easily be embedded in any source file, which is great for releasing one-file libraries without having to include a separate README or LICENSE file. Best of all, it's easy to grok. If developers should be able to consume open source as easily as pulling out books from a shelf, you really don't want to release software under a license that only a lawyer could love. Don't let MIT's concise nature fool you into thinking it's only used for toy projects: MIT is used in Rails, Mono, and the system for which it was originally written: X-Windows.

The MIT License looks like this:

<blockquote>
<p>Copyright (c) <year> <copyright holders>

<p>Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

<p>The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

<p>THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
</blockquote>