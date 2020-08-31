---
id: 1632
title: 'Rough Notes from Johan Ronsse&#8217;s Design for Developers Slides'
date: 2012-04-12T18:33:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1632
permalink: /rough-notes-from-johan-ronsses-design-for-developers-slides/
categories:
  - SoftwareDev
---
Clearing my desk and buried at the bottom of the pile was some notes I took a while ago while running through this slideshow. My notes are just capturing a few points to remind myself later and don't do the slides a speck of justice. So check out the slideshow instead, which <a href='http://www.slideshare.net/Wolfr'>Johan</a> went through after his talk and optimised for reading.

<div style="width:425px" id="__ss_10323363"> <strong style="display:block;margin:12px 0 4px"><a href="http://www.slideshare.net/Wolfr/design-for-developersonlineversionlong" title="Design for developers" target="_blank">Design for developers</a></strong> <iframe src="http://www.slideshare.net/slideshow/embed_code/10323363?rel=0" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe> <div style="padding:5px 0 12px"> View more presentations from <a href="http://www.slideshare.net/Wolfr" target="_blank">Johan Ronsse</a> </div> </div>

###Fonts and Layout

Avoid font-face for performance reasons. A good font is Verdana or Lucid Grande, fallback Lucida Sans Unicode.

Android: Droid Sans, WP7: Segoe UI

All text at least 14px
Consider 16px default
For Lucidea Grande or Verdana: 11-13px

Paras <= 60 characters wide

1.1 line-height for headings, 1.5 for paragraphs

Grid structure: think in units of 6.

###Light and Shadow

1-3px drop shadow

0-3px distance

Inner shadow when button is depressed

###Color

Recommended: [Hues app](http://itunes.apple.com/gb/app/hues/id411811718?mt=12)

Start with three colors

Blend foreground color with background color for text (ie don't just use pure gray/black if there's a colored background)

Dark gray with blueish tint looks good. Blue bottom is common (e.g. on GitHub)

Use at least as dark as #d5d5d5 on white background

Pay for good icons, e.g. Picons/Pictos/Fico

(This was just after I took the UX Bootcamp on Visual Design, and - look away now - I've also posted some [moodboards](http://imgur.com/a/SiG2w) from around then.) 