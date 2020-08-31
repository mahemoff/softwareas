---
id: 53
title: Printing and the Web
date: 2005-02-08T00:18:22+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=51
permalink: /printing-and-the-web/
categories:
  - HumansAndTech
---
There's lots of talk about "web 2.0" and indeed many good things are coming on. **But there also many anticipated web enhancements which are conspicuous by their absence.** I'm talking about things I found bothersome in the mid-1990s, things I had assumed would be fixed around the corner. Yet, they just don't seem to have emerged and it looks like web developers are stuck with them for a long time to come. Examples include HTML in general, the stateless nature of HTTP in general, and the shrine of inconsistent obfuscation that is javascript. Pretty fundamental stuff, huh? Anyway, my point here is printing.

We've gone from visions of the paperless office to printing like never before to the current situation: a decline in printing. At least that's my guess. And presumably it's thanks to email, PDAs, SMS messaging, bigger screens, and better collaborative tools such as document annotation and wikis. Yet, the decline in printing will be gradual and long. Paper still has many benefits: superior reading experience for many, legal relevance, safeguard for electronic storage.

*So as long as we expect printing to be around for a while, let's make printing the web a worthwhile experience*. **At present, there's HTML, which is difficult to print. And there's PDFs, which are designed for printing, but are difficult to read.** I'm not going to be Mr. SaveTheWorld and propose an uber-format ... I'm just going to suggest a few incremental improvements that would make life easier...

**Browsers should print HTML more gracefully:**
* **Print hyperlink URLs** Since reading occurs offline, print the linked URL beside any hyperlink. Like comments on slashdot do (although, by default, they only show the domain).
* **Print what I can see.** Many times, the browser is incapable of just printing what I can see. Thanks to funny javascript issues or attempts to reload dynamic pages, it just prints a blank page or a few lines. Not good enough. If you can display it on the screen, you can send it to the printer.
* **Handle frames properly.** Yeah, they're evil, but they're a fact of HTML life, and indeed a site like [bloglines](http://bloglines.com) shows how they can actually be very useful. All browsers should let me right-click inside a frame and allow me to print in that frame. Furthermore, when I try to print from the menu or toolbar, they should produce a thumbnail of the whole page, allowing me to visually select one or more frames for printing.
 (Frames are another of those that just won't go away ... frames had already been buried by the tech elite in the late 90s, who'd have thought a frame-based site like bloglines would be a [hot acquisition for 2005](http://www.micropersuasion.com/2005/02/ask_jeeves_buyi.html)?). 
* **Provide better previews.** Come on, you're about to print the thing! it can't be that hard to tell me how it will look or how many pages it will be.
* **Don't crash when i'm trying to print a moderately sized file** This one's firefox-specific.

**Browsers should render PDF more gracefully.** Since PDF actually achieves - or bypasses the above,  it could be a useful format for distribution. However, browsers just don't handle it very well, even when Acrobat is embedded into the browser.

I have just the one big suggestion here: stop dealing with PDFs using plugins, and instead render them as HTML. Google has been converting PDFs quite effectively for about five years now, and many tools do too. I'm sure I'm not alone when I click on the Google HTML version rather than the PDF version after performing a search. If Google can convert every PDF in the universe, the browser should be able to do it for a single document.

PDFs, with their discrete pages are very difficult to browse up and down. The font size is rarely anything to do with the browser's normal HTML size. All the browser tools you've come to know and love are either gone or mutated. Want to find some text in a PDF document? You'll have to do it the Acrobat way, not the browser way. And you can forget about all your browser-specific plugins, like language translation and bookmarklets. They'd be just as useful on PDF content, but it's not happening.

So the solution is simple: **browsers should be able to treat PDFs as HTML.** The Acrobat plugin can still be used for printing, so the PDF document could actually provide the best of both worlds. But for reading in a browser, HTML wins every time. And as the IText (Java PDF framework) FAQ [notes](http://www.lowagie.com/iText/faq.html#adobe), its perfectly within Adobe's conditions to create PDF tools. In any event, if Google can put converted PDFs on the web, what's to stop a browser from doing likewise?<!--3a1a2369937de1d946508134e0b0cb91-->