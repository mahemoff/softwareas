---
id: 1295
title: Whereupon HTML5 Doctype Messes with My Layout (and my head)
date: 2011-08-11T20:31:11+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1295
permalink: /whereupon-html5-doctype-messes-with-my-layout-and-my/
dsq_thread_id:
  - "383453344"
categories:
  - SoftwareDev
tags:
  - CSS
  - doctype
  - html5
---
TL;DR Use "5px" in your CSS, not just "5". It will be ignored with HTML5 doctype.

About to release my favicon tool and did the right thing with a &lt;!doctype html&gt;, which in Jade is simply <tt>!!! 5</tt>. I previously had no doctype.

Okay, but then I get some weird happenstance going down with the CSS. And Chrome devtools smugly crossing out style rules without telling me what's actually the matter. (For reasons having to do with the absurd time it takes to open a UK business bank account and my general lack of enthusiasm for paperwork, I'm currently using a computer so slow it's not economical to try this in Firebug.)

It took me a while to track down as I thought I'd made some other change in the meantime and simply didn't put it down to impulsively changing the doctype at some random moment of inspiration.

Specifically, I found with Chrome 14 at least that CSS needs a unit of measurement. You can't just say "5", you have to say "5px". I was actually saying "5" and assuming Stylus would translate it to 5 pixels. Serves me right anyway for using absolute measurements and now I've updated everything to use "em" units.

I also discovered negative padding is not possible (regardless of doctype). And I agree with [Aza](http://weblogs.mozillazine.org/asa/archives/2007/12/css_negative_pa.html), that sucks. There's definitely cases where it would save work and avoid adding wrapper elements just for the sake of it.