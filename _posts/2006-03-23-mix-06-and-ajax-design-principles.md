---
id: 283
title: 'Mix &#8217;06 and Ajax Design Principles'
date: 2006-03-23T03:04:11+00:00
author: admin
layout: post
guid: http://www.softwareas.com/mix-06-and-ajax-design-principles
permalink: /mix-06-and-ajax-design-principles/
dsq_thread_id:
  - "447575199"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Design
  - Links
  - Mix06
  - Patterns
  - Usability
  - Web
  - Web2.0
---
<a href="http://mix06.com"><img src="http://img69.imageshack.us/img69/998/mix7gm.png"></a>

<a href="http://www.tisgoud.nl/blog/PermaLink,guid,5bc34eaa-025c-406b-8ccf-787ec143eb26.aspx">'Tis Goud</a> reports from <a href="http://mix06.com">Mix '06</a>, Microsoft's web bash currently happening in Vegas.  <strong><a href="https://content.mix06.com/content/SessionView.aspx?TopicID=f27514b7-8391-444b-85b5-f491f6ef87b5">One of the presentations</a> focused on the most important thing about Ajax: Usability.</strong>


<a href="http://www.tisgoud.nl/blog/PermaLink,guid,5bc34eaa-025c-406b-8ccf-787ec143eb26.aspx">
<img src="http://img146.imageshack.us/img146/2534/hao8mt.png" align="right" style="padding: 6px;"></a>

<blockquote>
<p>The session started with referencing two sites with information on:</p>
<ul>
    <li><a href="http://ajaxpatterns.org">Usabillity Patterns</a>, Michael Mahemoff
    <li> <a href="http://www.tisgoud.nl/blog/ct.ashx?id=5bc34eaa-025c-406b-8ccf-787ec143eb26&url=http%3a%2f%2fwww.baekdal.com%2farticles%2fUsability%2fXMLHttpRequest-guidelines">Usabillity Guidelines</a>, Thomas Baekdal
</ul>
</blockquote>

Thomas's guidelines were the first serious look at Ajax usability and <a href="http://softwareas.com/ajax-patterns">a big inspiration</a> for the Ajax Patterns.

The patterns and the principles were apparently distilled to this list:
<blockquote>
<ul>
    <li>Feedback</li>
    <li>Predict</li>
    <li>Preserve</li>
    <li>Share</li>
    <li>Controls</li>
    <li>Separate</li>
</ul>
</blockquote>

If anyone has more detailed info on this discussion, please let me know!

As it happens, the third chapter of "Ajax Design Patterns", the overview to the patterns themselves, explicitly identifies principles on which the patterns were based. <strong><a href="http://mahemoff.com/paper/principles/">Principles and patterns</a> go hand-in-hand, so any pattern language I've worked on always comes with a set of principles, an explicit reference point for people to grasp where the patterns are coming from.</strong> You can even (with some energetic hand-waving) look at the patterns as being defined around the principles: <strong>"These patterns are written such that if you follow them, your system will adhere to these principles".</strong>

Anyways, the principles are broken into two groups: Usability Principles and Software Design Principles. Maybe I ought to podcast them sometime.

These are the <strong>Usability Principles for Ajax</strong>.

<ul>
<li>Follow Web Standards</li>
<li>The Browser is Not a Desktop</li>
<li>If it's Different, Make it Really Different</li>
<li>Provide Affordances</li>
<li>Smooth, Continuous, Interaction</li>
<li>Customisation</li>
<li>Make it Fun</li>
</ul>

These are the <strong>Software Design Principles for Ajax</strong>.

<ul>
<li>Embrace Javascript</li>
<li>Accept Workarounds Where Necessary</li>
<li>Tame Asynchrony</li>
<li>Develop for Compatibility</li>
<li>Reduce Bandwidth</li>
<li>Deal with Latency</li>
<li>Partition into Multiple Tiers</li>
<li>Go Easy on the Browser</li>
<li>Practice Graceful Degradation</li>
</ul>

It's funny. The very first thing I think of when I see stuff like this is along the lines "SHOW ME THE PATTERNS!!!!". I've got no patience for motherhood statements like 'Tame Asynchrony'. But the reason for this annoyance is because you usually see these kind of principles in the absence of any explanations, examples, or patterns. Once it's apparent that the principles are merely a background to more concrete advice, their presence has been justified.