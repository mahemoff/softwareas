---
id: 262
title: Ajax Patterns in the Pattern Community Radar
date: 2006-02-04T10:50:17+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-patterns-in-the-pattern-community-radar
permalink: /ajax-patterns-in-the-pattern-community-radar/
enclosure:
  - |
    http://brain.cs.uiuc.edu/SAG/2006-01-30-Ajax.mp3
    81625216
    audio/mpeg
  - |
    http://brain.cs.uiuc.edu/SAG/2006-01-30-Ajax.mp3
    81625216
    audio/mpeg
dsq_thread_id:
  - "386119510"
  - "386119510"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Links
  - Patterns
---
I'm pleased that AjaxPatterns.org seems to have entered the pattern community radar in the past couple of months (or maybe earlier, but that's the impression I'm getting) ...

<h3>Workshop on Ajax Patterns</h3>

Ralph Johnston (of GoF Design Patterns fame) runs a regular patterns reading group/workshop and they've been looking at the Ajax patterns. Fortunately, they release the discussions online, which is a great, if unexpected, source of feedback for me! (I had some volume issues and need to listen again after pumping up the MP3s, so I won't comment on the content yet). The discussion is a mix of general Ajax talk (most participants are approaching this as Ajax programming newbies) and critical analysis of the patterns.
<ul>
<li><a href="http://brain.cs.uiuc.edu/SAG">Directory of all pattern workshop MP3</a> (where I assume you'll find a second workshop too in a few weeks).
</li>
<li>Direct link to the discussion: http://brain.cs.uiuc.edu/SAG/2006-01-30-Ajax.mp3 </li> (which I won't link to directly because a future version of WordPress might incorporate it into my podcast feed :-).
</ul>

<h3>Brian Foote: Calling a pattern a pattern</h3>

(I'm using this as a springboard to rant on some general pattern stuff ...)

Pattern veteran <a href="http://www.laputan.org/catfish/archives/000139.html">Brian Foote</a> (also in the discussion above) says that [JJG's definitive Ajax article](http://www.adaptivepath.com/publications/essays/archives/000385.php) is "quite pattern-like" and apparently concurs with [James Governor's](http://www.redmonk.com/jgovernor/archives/001186.html) assertion that Ajax is a pattern. Of AjaxPatterns, he says:

<blockquote>
Now, <a href="http://mahemoff.com/">Michael Mahemoff</a> has exhibited no compunction in calling a <i>pattern</i> a <i>pattern</i>. <a href="http://www.cincomsmalltalk.com/userblogs/ralph/View.ssp">Ralph Johnson</a> pointed out <a href="http://ajaxpatterns.org">this</a> website a few weeks ago for a <a href="http://softwareas.com/">forthcoming</a> <a href="http://www.softwareas.com/ajax-design-patterns-book">book</a> on 
<a href="http://ajaxpatterns.org">Ajax Patterns</a>. It is tastefully rendered, and quite engaging. I commend it to the reader's attention. 
</blockquote>

Yes, Ajax has always been a pattern to me. In the notes for [last April's Ajax 
podcast](http://www.softwareas.com/ajax-podcast), I referred to it as an "architectural style", which I use synonomously with "architectural pattern" (other examples would include "MVC", "Blackboard", etc; I think I originally got this idea from Buschmann et al's System of Patterns V1). A few months ago, I bit the bullet and added an "Ajax App" pattern to AjaxPatterns. Not all pattern languages need a root, but it makes sense in this case to have something that ties everything together.

Is "Ajax App" a pattern? I say it is because it's a well-proven solution to a recurring problem. Some say that patterns should provide some insight, and Ajax App is just too obvious a solution nowadays to call it a pattern. It would have been fine for JJG to introduce "Ajax App" as a pattern in early-2005, but what's the value of an "Ajax App" pattern in the enlightened era of early-2006? I would mostly agree with that if the "Ajax App" were published in isolation. But it's not. It's published in the context of 68-odd patterns on all things Ajax, as the pattern that holds them together, and many of the patterns refer back to it. It's a high-level, architectural, pattern, which can be decomposed into lots of smaller patterns that are also documented. It has the essense of being unobvious, even if the buzz of the past year now renders it obvious.

Another way to say it: I'm not really comfortable with the argument that patterns must be unobvious. In some contexts, there's still many benefits to gain from using a pattern construct to document something that may actually be obvious. I emphasise this because it not only explains why "Ajax App" is a pattern in AjaxPatterns, but also <a href="http://ajaxpatterns.org/XMLHttpRequest_Call">XMLHttpRequest Call</a>, <a href="http://ajaxpatterns.org/Display_Morphing">Display Morphing</a>, etc. They are obvious things to do because they fall out directly from the technology ... What else are you going to do with an XMLHttpRequest but issue a call??!!!! But just because they are obvious, doesn't mean we can't document them. They completely integrate into the structure of the overall Ajax Patterns language, with lots of useful links to and from them. They can completely be described by the standard pattern notations. They give us a suitable, distinctly named, **easily discovered**, container to elaborate on the technologies involved, the decisions you have to make, and so on. Which is why you'll find XMLHttpRequest's API in the XMLHttpRequest Call pattern, and an overview of the DOM in the Display Morphing pattern.

For the record, I'm also not comfortable with the argument that patterns must be proven. Again, I think the argument for provenhood comes from a well-intentioned attempt to keep the patterns relevant and useful. But I'd rather lay out all the patterns on the table, present whatever evidence exists, and let the reader decide how they stack up. For that reason, you have some patterns like <a href="http://ajaxpatterns.org/Host-Proof_Hosting">Host-Proof Hosting</a> that are unproven, but promising enough to point out. Again, they fit right into the structure, they are easily documented with a standard pattern structure, and they are a suitable **easily discovered** namespace to elaborate on the concepts as well as facilitate a discussion of whether it's worth implementing, and 

I'm not a "pattern theoretician", so these ideas perhaps don't hold up to current thinking. I discovered early on that the patterns community generally avoids too much meta-discussion  on patterns and I've always respected that view.  My PhD never defined a pattern as a "vector of fields 1..n" or a pattern language as a "directed, acyclic, graph", even though some academics felt it would have been the right thing to do. I take a pragmatic view of patterns - "Are they useful or not" is really my main interest, and I think that's reflected in the comments above. I don't mind if you call "XMLHttpRequest Call" a "guideline" instead of a "pattern", but I think you can see why I choose to call it a pattern - it's documented that way and it happens to live within a larger system of patterns.

All this comes down to fuzzy thinking instead of strict dychotomies - the same reason I often talk about "how Ajaxian" a system is, rather than "Is it Ajax or not". Same for a pattern - "how pattern-like is it" rather than "Is it a pattern or not"?  I find strict definitions futile, which is why you'll usually find me disclaiming and apologising profoundly whenever I utter one.

<h3>Erich Gamma</h3>

From <a href="http://www-128.ibm.com/developerworks/blogs/dw_blog_comments.jspa?blog=396&entry=106358">Brian Higgins</a>:
<blockquote>
I've been working on some Ajax stuff lately and this morning I was complaining to patterns guru Erich Gamma that I hadn't seen any good design pattern resources for Ajax. He pointed me to this site which looks good:

http://ajaxpatterns.org/

Would have never guessed that one!
</blockquote>

<h3>Interview with Wally McClure</h3>

Not specifically patterns, but I also want to point out that Wally McClure from the ASP.Net Podcast recently interviewed me (fortunately for me not about ASP.Net, which would have been pretty brief!). I've had various mail conversations with Wally, who's writing a book on Ajax and ASP.Net, so it was good to catch up and talk Ajax. Unfortunately, we had some skype issues, so we didn't end up talking too in-depth. (BTW Both Wally and I had Skype issues. Is Skype seriously ready to be the telephone platform for the next decade? Seems way flakey and lacking in support to me! I submitted a detailed error report a while back and received nothing, despite the fact that I pay around $50 a month for calls. The error message is something about an unauthorised resource, as I recall, which a lot of googling tells me is a file permission error, perhaps, but Skype's log contains zero information about the resource in question even though people have been experiencing the problem for a year or more.)<!--f383ebfacc528bfc347a355904c7067a-->