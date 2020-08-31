---
id: 1887
title: Bitten By Significant Whitespace
date: 2013-02-01T02:35:10+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1887
permalink: /bitten-by-significant-whitespace/
categories:
  - SoftwareDev
tags:
  - CoffeeScript
  - touch
---
I've come to love significant whitespace since using it in CoffeeScript. (I'd dismissed it due to generally not getting on with Python, but really that's for other reasons.) By eliminating the need for { }, code is more to the point.

However, significant whitespace is playing with fire and I just got burned.

<script src="https://gist.github.com/4688710.js"></script>

The code helps to tailor sidemenu behaviour for a touch device. Anyway, the final `false` was wrongly indented. It should have been indented by 2 more characters to appear directly under the other 3 lines.

It must have been a quick edit or something, but the net effect was forms couldn't be submitted when on a touch interface. I couldn't quickly track it down, so made some workarounds to get things working, but then I realised it was happening on all forms, so looked into it more.

Lessons:
* Be very careful changing any Coffee indents
* `Modernizr.touch` would be a good starting point to search for the cause of any bugs like this.