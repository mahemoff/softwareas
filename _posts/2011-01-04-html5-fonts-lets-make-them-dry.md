---
id: 1057
title: 'HTML5 Fonts: Let&#8217;s Make them DRY'
date: 2011-01-04T02:04:19+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1057
permalink: /html5-fonts-lets-make-them-dry/
dsq_thread_id:
  - "375158668"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Agile
  - CSS3
  - Fonts
---
<h3>The Problem</h3>

Much fun can be had designing with the ever-increasing universe of fonts offered by directory's like <a href="http://code.google.com/webfonts">Google's</a>. <a href="softwareas.com/photoshop-tamagotchi">Photoshop Tamagotchi</a> is a thing of the past as you can rapidly iterate with a few keystrokes. But it's still a few keystrokes too many ...

A niggle with CSS3 fonts is they involve some redundancy. Here's a real-world example:

[css]
@font-face { font-family: Delicious; src: url('Delicious-Roman.otf'); }
@font-face { font-family: Delicious; font-weight: bold; src: url('Delicious-Bold.otf'); }
h3 { font-family: Delicious, sans-serif; }
[/css]

What happened to <a href="http://en.wikipedia.org/wiki/Don't_repeat_yourself">Don't Repeat Yourself</a>? We have "Delicious" mentioned five times here! If we switch from the "Delicious" font to the "Pinboard" font, we'll need to make five changes. And not everyone uses vim, yo. Moreover, we'll need to locate a suitable font, e.g. Pinboard, and download it.

I get it, this level of indirection serves a purpose. We can give a handle to the font once and then use that everywhere else. Heck, we could even continue to call the font "Delicious", but surreptiously switch the "src" to "Pinboard-Roman.otf". But that wouldn't be very nice, would it?

Now, a font directory like Google solves part of the problem by explicitly allowing you to link cross-domain to Google. In fact, if you want, it will even generate the stylesheet for you. But you'll still have the same DRY issue in your CSS - for each new font, you'll need to include the stylesheet *and* use it in your CSS.

<h3>The Solution</h3>

Bottom line, I decided to make this crazy snippet, by manually walking through the font directory and picking out every single possible font:

[html]
<link href="http://fonts.googleapis.com/css?family=Droid+Sans|Lobster|Droid+Serif:regular,italic,bold,bolditalic|Nobile|Yanone+Kaffeesatz|PT+Sans:regular,italic,bold,bolditalic|PT+Sans+Caption:regular,bold|PT+Sans+Narrow|Reenie+Beanie|Tangerine:regular,bold|Molengo|OFL+Sorts+Mill+Goudy+TT:regular,italic|Vollkorn:regular,italic,bold,bolditalic|Cantarell|Inconsolata|Crimson+Text|Arvo:regular,italic,bold,bolditalic|Cardo|Neucha|Neuton|Droid+Sans+Mono|Cuprum|Old+Standard+TT:regular,italic,bold|Philosopher|Tinos:regular,italic,bold,bolditalic|Josefin+Sans:100,100italic,light,lightitalic,regular,regularitalic,600,600italic,bold,bolditalic|Arimo:regular,italic,bold,bolditalic|Josefin+Slab:100,100italic,light,lightitalic,regular,regularitalic,600,600italic,bold,bolditalic|Allerta|Geo|Allerta+Stencil|Puritan|Puritan:regular,italic,bold,bolditalic|Cousine:regular,italic,bold,bolditalic|UnifrakturMaguntia|Bentham|IM+Fell+DW+Pica:regular,italic|IM+Fell+English:regular,italic|IM+Fell+English+SC|IM+Fell+DW+Pica+SC|IM+Fell+Double+Pica+SC|IM+Fell+Double+Pica|IM+Fell+Great+Primer+SC|IM+Fell+Great+Primer|IM+Fell+French+Canon|IM+Fell+French+Canon+SC|Coda:800|Raleway:100|UnifrakturCook:bold|Covered+By+Your+Grace|Just+Me+Again+Down+Here" rel="stylesheet" type="text/css" />
[/html]

I'll repeat that below for ease of cut-and-paste:

&lt;link href="http://fonts.googleapis.com/css?family=Droid+Sans|Lobster|
Droid+Serif:regular,italic,bold,bolditalic|Nobile|Yanone+Kaffeesatz|
PT+Sans:regular,italic,bold,bolditalic|PT+Sans+Caption:regular,bold|
PT+Sans+Narrow|Reenie+Beanie|Tangerine:regular,bold|Molengo|
OFL+Sorts+Mill+Goudy+TT:regular,italic|
Vollkorn:regular,italic,bold,bolditalic|Cantarell|Inconsolata|Crimson+Text|
Arvo:regular,italic,bold,bolditalic|Cardo|Neucha|Neuton|Droid+Sans+Mono|
Cuprum|Old+Standard+TT:regular,italic,bold|Philosopher|
Tinos:regular,italic,bold,bolditalic|
Josefin+Sans:100,100italic,light,lightitalic,
regular,regularitalic,600,600italic,bold,bolditalic|
Arimo:regular,italic,bold,bolditalic|
Josefin+Slab:100,100italic,light,lightitalic,regular,
regularitalic,600,600italic,bold,bolditalic|
Allerta|Geo|Allerta+Stencil|Puritan|Puritan:regular,italic,bold,bolditalic|
Cousine:regular,italic,bold,bolditalic|UnifrakturMaguntia|Bentham|
IM+Fell+DW+Pica:regular,italic|IM+Fell+English:regular,italic|
IM+Fell+English+SC|IM+Fell+DW+Pica+SC|IM+Fell+Double+Pica+SC|
IM+Fell+Double+Pica|IM+Fell+Great+Primer+SC|IM+Fell+Great+Primer|
IM+Fell+French+Canon|IM+Fell+French+Canon+SC|Coda:800|Raleway:100|
UnifrakturCook:bold|Covered+By+Your+Grace|
Just+Me+Again+Down+Here" rel="stylesheet" type="text/css" /&gt;

Now include that in your CSS and you can freely use whatever font you want, whenever you want:

[css]
h3 { font-family: Neucha, sans-serif; }
div { font-family: "Reenie Beenie"; }
[/css]

<h3>Production Use</h3>

I haven't tested it, but I'm informed modern browsers will thankfully download only the fonts they need, so this is actually a viable solution for  sites which will be frequented only by modern browsers, though obviously the snippet itself is too big for sites where performance is critical.

Unfortunately, IE6-IE8 will actually download every single font specified! So really, you should only be using this for development, and ensure production sites only declare the fonts they need. However, don't lose site of DRY! In the spirit of Agile, DRY, and Continuous Integration, it would still be worth looking at ways to automate that process, e.g. with a server-side solution that generates the minimalist "link" tag.

Of course, the snippet is limited only to the Google fonts, good enough for my aesthetically-challenged purposes, but the principle could be generalised to encompass other font directories. Or someone in a company which has licensed and/or issued a standard set of fonts via their style guide, could also generate a company-specific snippet fot this purpose, containing all fonts. They could then make this a standard stylesheet which could be linked to from any HTML document.