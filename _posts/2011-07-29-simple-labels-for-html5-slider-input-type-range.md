---
id: 1265
title: Simple Labels for HTML5 Slider (Input Type = Range)
date: 2011-07-29T07:21:45+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1265
permalink: /simple-labels-for-html5-slider-input-type-range/
dsq_thread_id:
  - "375140675"
categories:
  - SoftwareDev
tags:
  - CSS
  - html5
  - jade
  - Slider
  - stylus
---
For a favicon tool I'm working on, I tried using an HTML5 slider for the first time and was surprised to learn there's no labels. Looked at a couple of shims out there, but they are _just_ shims and don't include labels either. So d-i-y ...

The slider looks as below, and the CSS doesn't make any assumptions about length of the slider or the two labels.

<img src="http://farm7.static.flickr.com/6011/5987096578_568d4a012f_o.png" />

The labels are generated using the old margin 50% wrapper trick, as you can see in the following Jade markup and Stylus CSS:

<pre>
input.rangeOption(type="range",min="0",max="1",step="0.1",title="Transparency: 0 to 1")
  .labels
    .minLabel
      span solid
    .maxLabel
      span transparent
</pre>

[css]
.rangeOption
  float left
  margin-left 2em
  input
    display block
  .minLabel
    float left
    span
      margin-left -50%
  .maxLabel
    float right
    span
      margin-left 50%
[/css]