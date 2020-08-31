---
id: 1303
title: Announcing Faviconist
date: 2011-08-31T00:09:46+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1303
permalink: /announcing-faviconist/
dsq_thread_id:
  - "400450058"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Announcement
  - Canvas
  - Favicon
  - Favicon Generator
  - Faviconist
  - html5
  - Node
---
<a href="http://faviconist.com"><img alt="faviconist screenshot" title="click for visit faviconist" src="http://faviconist.com/favicon-generator400x275.png"/></a>

I have made a new [Favicon generator](http://faviconist.com), Faviconist. Since most favicons are just a letter with some colour theme, I found it crazy to have to open up a photo editor every time I wanted a new favicon. Or alternatively, it's easy enough to convert an image with ImageMagick, but most images don't scale down nicely to a tiny icon! So the aim here is not an editor as such, but a true "favicon generator".

### Using Faviconist

To create a favicon, it's as simple as typing the first letter of your website. But you probably don't want the default colour scheme, so it's easy enough to tweak. Under the covers, Favicon has a concept of a "FillStyle" and both foreground and background are instances of FillStyle, so they have the same flexibility. You can have a solid fill style (just a single colour), a linear gradient, or a radial gradient.

For simplicity, Linear gradients don't have stops (it's just a linearly increasing spectrum from start to finish), though you can choose the direction. And in the same sprit of simplicity, radial gradients may only begin at some points, and their span is fixed. The guiding principle here is "YAGNI" - You Ain't Gonna Need It. I'm catering for the 95% of people who don't want to micro-design their icons; the rest will still need to resort to PhotoShop et al.

The preview images are PNGs, which can easily be downloaded directly. However, another gripe of mine is the whole thing of downloading to hard drive and uploading back to a server somewhere else. Hot-linking, aka "bandwidth theft", is rightly a problem for the original image host...but it's a shame the only way we can deal with it is to silo everything. ([A parallel vision of the web](http://en.wikipedia.org/wiki/Project_Xanadu), which might have almost succeeded and still might, saw it more as embedded content than a collection of copies and links.) In this case, it's only favicons, so I'll just say hot-link and be merry. When you click "Save Favicon", it saves the icons on my server and you can just cut-and-paste into your own project.

I hope this is useful for quick hacks and hackathons, where favicons are often forgotten! These days Favicons are more useful than here. Of [many reasons to use a favicon](http://faviconist.com/about), things one might forget are: they're used on third party sites like Google Plus, tabbed browsing is super-popular these days; if you don't provide favicons, you'll get 404s in your log files.

And here's a little tip for you - don't just use letters. Try special characters, and don't just limit yourself to ASCII. You have the [entirety of Unicode](http://en.wikipedia.org/wiki/List_of_Unicode_characters) at your disposal!

![](http://farm7.static.flickr.com/6132/6096649447_e0baab5b97_o.png)

![](http://farm7.static.flickr.com/6079/6096651351_3c3393b25c.jpg)

![](http://farm7.static.flickr.com/6081/6098539984_c2b1a1e203.jpg)

### How Favicon Works

Buzzword Bingo time. There are a number of technologies at work here:

* **HTML5 Canvas** In the past, a site like this would have to be powered by the server - every change would require a long wait for the server to generate a new image. But now, we can do it in real-time, in the browser, using Canvas. The only server interaction is conversion to ".ico"; unfortunately, Canvas will output to PNG, but not ICO. And while a JavaScript ICO encoder is certainly a possibility, no-one has yet written one.

* **Canvas Text** To draw text, Faviconist uses Canvas's fillText method. e.g. <tt>context = canvas.getContext('2d'); context.fontStyle = '25px arial'; context.fillText('Yo!')</tt>. When [Ace Editor](http://ace.ajax.org/) effort got started (called Bespin), in the early days of canvas, text support was patchy. But now it's very well supported.

* **MeasureText Library** I thought Faviconist would be easy because I thought there would be simple metrics for fonts. Turns out canvas's measureText() returns [a "TextMetrics" object](http://www.whatwg.org/specs/web-apps/current-work/multipage/the-canvas-element.html#textmetrics), and guess what TextMetrics contains:

<pre>interface TextMetrics {
  readonly attribute double width;
};</pre>

Huh? We can only find the text's width, not its height. And as a I went down the path, I learned you can't just say "draw this text with its top-left at (0,0)". To center the font, as we do in Faviconist, we actually need to determine text offset as well - left and top.

So I built the [MeasureText library](https://github.com/mahemoff/measuretext). It works as a drop-in replacement (~shim) for the built-in HTML5 Canvas MeasureText mechanism, and also provides a new convenience function not requiring an existing canvas. It works by drawing the text and scanning the resulting bitmap to get a true representation of the metrics. Using this, and with a little geometry, it's possible to center text.

* **Favicon Library** Figured it would be cool to show a preview of the favicon by changing the site's actual favicon! For which I used ye olde [Favicon library](http://faviconist.com/favicon-library), which I originally [created via this blog](http://softwareas.com/dynamic-favicons) and I've now officially moved to Faviconist.com. The library also incorporates a new "badge" feature, so you can show number of pending emails, etc. Go try the [demo](http://faviconist.com/favicon-library)!

* **Font Selection** You can choose fonts, with the fonts coming from [the Google Font Directory](http://www.google.com/webfonts). It wasn't feasible load all fonts, so they're loaded dynamically, but I wanted to show previews ... so there's a script to build a 38,000 pixel sprite map! It's loaded after the page loads, with a canvas-based check to see if it loaded successfully (since it doesn't work on Firefox). To show it in a dropdown, I used a fork of the [Chosen](http://harvesthq.github.com/chosen/) library, a fork which retains the class of each option in the select list.

* **Chrome Frame** Didn't want to support IE6-IE8, so introduced Google Chrome Frame, based on the code in [HTML Boilerplate](http://html5boilerplate.com/), but increasing the version check from 6 to 8.

* **JavaScript Libraries** Faviconist uses several useful libraries: jQuery, Underscore, Backbone, and [jQuery Tools](http://flowplayer.org/tools/). And just to say, jQuery Tools is the very picture of Developer Experience heaven. Great explanations, many easy-to-follow demos, lots of options...and a CDN for the libraries.

* **NodeJS, Connect, Express** The server is NodeJS running the Express-Connect stack. Considering that the app is almost all client-side, I spent a ton of time getting up to speed with this stack, partly due to performance optimisatins, and partly due to the next point ...

* **Jade, Stylus, Kaffeine** Being a fan of DRY, I'm very happy to be using higher-level abstractions of HTML, CSS, and JavaScript. I certainly am happy with Jade, with the exception of dropping in raw HTML script snippets. And Stylus is absolutely awesome. Kaffeine makes JavaScript much easier, though I've found it difficult to incorporate everywhere because the ecosystem is very much geared around CoffeeScript. e.g. Connect comes with a default CS compiler, Nodemon (a node watch-and-run-tool by Remy Sharp) supports CS, there's a ton of doco about getting CS working with things. So that was really the biggest challenge. I mainly wanted Kaffeine because I'm not such a fan of significant whitespace, but the ecosystem's preference for CoffeeScript did present challenges.

I hope you enjoy Faviconist. It's a work in progress, so please leave feedback if you have suggestions.