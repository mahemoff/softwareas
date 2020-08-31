---
id: 477
title: 'Using 280Slides (Ajax slideshow maker): Real World Experiences'
date: 2008-08-13T23:24:07+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=474
permalink: /using-280slides-ajax-slideshow-maker-real-world-experiences/
dsq_thread_id:
  - "375573934"
categories:
  - SoftwareDev
tags:
  - 280Slides
  - Ajax
  - Javascript
  - Keynote
  - Review
  - Slideshows
  - Usability
---
<a href="http://280slides.com"><img src="http://picupper.com/2008/08/13/2628847277_f0dd16c0e1.jpg"/></a>

I used 280slides.com for a quick presentation today at the London Javascript meetup. (The usual Jobsesque slides - usually one phrase plus an optional image.)

The tool is very cool, as initial reviews suggested, but most of those folks had not used it in a real world situation. The tool has it's complications when you use it for real.

What's good:

* Looks cool and OSX/Keynote like, but not slavishingly following the desktop in a way which would detract from usability
* Great sharing and embedding options - can download as ppt, pptx (powerpoint 2007), pdf, and open document...and moreover, can view it full-screen, send it to slideshare, and embed it on a web page.
* Has all the basic tools you need
* Has undo and redo with a long history.
* Supports OSX key bindings, i.e. uses the <a href="http://en.wikipedia.org/wiki/Command_key">command key</a> (ie the apple key) instead of what most web apps do, which is to use the ctrl-key even on OSX. (On the whole, there's a need for a really great Ajax/Javascript key event library to do stuff like this automagically.)
* Can easily do a slick full-screen mode presentation, using the <a href="www.barbariangroup.com/software/plainview_app_1_0">PlainView browser</a>, as noted on <a href="http://blog.280north.com/2008/06/19/go-fullscreen-with-plainview/">the 280slides blog</a>.
* Supports themes. (Themes is one rare area where the Ajax/web model makes life very easy for developers of desktop-like apps - just change the CSS style. If only life was so simple for the developers of the original desktop-like apps, where CSS-like functionality is usually lacking.)

What could be improved - this is all intended as constructive criticism. The team's effort to date shows they are extremely talented Ajaxers and I have no doubt every one of the following can potentially be rectified in the coming months, provided they have enough will and bandwidth.

* Cut-and-paste - this one really got me. Cut-and-paste is something we do all the time when making slideshows. The problem here is that elements are pasted directly on top of each other, so you can't tell if it's been pasted or how many times it's been pasted (and you may well have several, as it's likely you'll be hitting command-v a few times, since there's no feedback). This is exacerbated by the delay involved - sometimes takes a second or two to make the paste, so when you try to start dragging the copy, you might instead end up dragging the sole, original, element.
* AFAICT cut/paste/copy are available only as keyboard shortcuts. There's no toolbar/menu item. This exacerbates the previous problem. With "paste" lacking immediate visual feedback, you'd at least want a button you can click instead of relying on the keyboard shortcut, which feels less assuring (mainly because keyboard shortcuts are still a bit of a novelty on the web). And of course, the other problem is that users aren't aware the keyboard shortcuts are available.
* Saving - it's not clear if auto-save is present. It certainly should be. They need some sort of status message for this, or an auto-save checkbox (though I think it should always be on).
* Undo isn't perfect. Sometimes the undo skips the most recent action and instead undoes an action before that. This often happens to be an action on a different slide - it's good that it jumps back to that slide, but you can easily lose your place and makes it difficult to then go and manually undo the action you actually wanted to undo.
* It's fairly processor-intensive. This isn't really a fair criticism, because it's too much to expect an app like this to be gentle on resources. Still, I did struggle running it on a 3 year old powerbook and that will affect some users. On the bright side, it's very snappy on a newly booted Firefox running on a more modern Macbook.
* When you select text to change it, the text becomes grey to highlight it - thus making it impossible to see any new colour scheme you've chosen. Whenever I tweaked background or foreground colour, I had to keep unselecting the text, viewing it, and then re-selecting the text and change the colour again.
* Text blocks don't auto-expand/shrink when you change the text size. You must manually resize.
* As you'd expect, there's no support for a lot of the more advanced features. Some people would say those features are unnecessary, but personally I do find they do make an impact in live presentations and can often help to convey info in subtle ways. I'm talking about features like shadows, gradients, round corners. I know, it's all just "bling-bling web 2.0 eye candy noise", but really they're essential if your aim is to keep your slides in the visual - rather than literary - realm. Also, there are some more basic features not yet implemented, e.g. borders for images and shapes, and the ability to crop.
* Images can load quite slowly, and again, there's no progress indicator. Unloaded images are shown just as a grey block, so viewers mightn't be aware that an image is loading in that spot.
* As I was writing this post, I opened up the slideshow and somehow it added a blank textboxes to every slide. Don't ask me how or why. The existing text somehow had shifted up to the top of the page, and had been resized to one line. I think it somehow had tried to apply a standard slide template (title and main text area), whereas my slides are mostly just one line in the middle of the slide.

Anyway, it's already usable and has huge potential. Long may 280slides rock! I only hope that if they're acquired, the innovation keeps happening.