---
id: 1813
title: 'Amazon&#8217;s Pure CSS Solution to Avoid Cutting Off Text'
date: 2012-08-15T11:18:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1813
permalink: /pure-css-solution-to-avoid-cutting-off-text/
categories:
  - SoftwareDev
tags:
  - CSS
  - CSS3
  - gradients
---
<a href='http://i.imgur.com/jfIL4.png'>![](http://i.imgur.com/jfIL4.png)</a>

Amazon [is using](http://www.amazon.co.uk/CompTIA-Certification-Seventh-220-701-220-702/dp/0071701338/ref=sr_1_15?s=books&ie=UTF8&qid=1345027069&sr=1-15) a nice CSS trick to truncate a text block without showing half-lines (like someone cut the document horizontally). The problem is that CSS "overflow: hidden;" is a crude creature that will brutally cut lines off halfway through like a 1970s dot-matrix printer. There's no "overflow hidden, but jeez be gentle about it okay" property. So this is a workaround, but it does impose a change on the UI...the fading text on the bottom.

Using Devtools for the image below, I've enhanced the mask with outline and gradient colour, and also filled the block with text to build a continuous paragraph on the bottom.

<a href='http://i.imgur.com/hUC6h.png'>![](http://i.imgur.com/hUC6h.png)</a>

There's a semi-transparent gradient mask in front of the content. The mask is mostly clear, but has a white band on the bottom 15%. This band is turquoise for illustration purposes here. So this bottom band covers up text on the next line without occupying too much whitespace. You'll notice the band starts where the bottom line ends. So the bottom line is already fading, and then BOOM! It's all white below that.

The mask is 50 pixels, so there will be about 45 pixels (85% of 50px) transition from full text to fully-transparent text, followed by about 5 pixels of white.

A side note is the layout technique for the mask. Probably basic for most CSS designers, but not how I would have done it. It's simply using standard flow, but with position: relative to shift the mask up 50px, and a 50px negative margin to ensure the mask doesn't actually affect the flow. (I would have done it by making the whole thing position relative, and absolute elements inside it. This technique is much simpler.)

[I found this technique](https://plus.google.com/106413090159067280619/posts/PUsQmbh68rr) via [StackOverflow](http://stackoverflow.com/questions/9776627/set-div-height-so-text-is-not-cut-or-sliced-horizontally) a little while ago, as mentioned here earlier, so I was chuffed to spot it in the wild, and on Amazon no less.

Update: [Syd Lawrence points out](http://twitter.com/sydlawrence/statuses/235854202180612096) that it's worth using <tt>pointer-events: none</tt> on the mask. This is the CSS property that makes the front layer porous, allowing mouse clicks to cheekily slip through to the element behind it.