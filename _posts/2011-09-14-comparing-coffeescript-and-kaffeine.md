---
id: 1301
title: Comparing CoffeeScript and Kaffeine
date: 2011-09-14T10:09:57+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1301
permalink: /comparing-coffeescript-and-kaffeine/
dsq_thread_id:
  - "414154306"
categories:
  - SoftwareDev
tags:
  - CoffeeScript
  - Javascript
  - JS Dialects
  - Kaffeine
---
![](http://picupper.com/2011/09/14/tower.jpg)

I've recently been Node web programming and as a long-time proponent of DRY, I'm more than happy about the [Alt-JS](http://altjs.org) movement that has taken the webdev community by storm over the past six months, along with alt-HTML and alt-CSS.

We [used CoffeeScript](http://softwareas.com/is-this-what-the-app-of-2015-looks-like-html5-coffeescript-less-webstore-phonegap-apparatio) and Less for HN Reader. [Faviconist](http://faviconist.com) is built on Jade for HTML, Stylus for CSS, and Kaffeine for JavaScript. I'm now doing a project in CoffeeScript for comparison, and because I found Kaffeine wasn't as much of a finger-typing saver as I'd hoped for. Also, CoffeeScript has a huge ecosystem at this point. There are definitely great things about both, and indeed they are more similar to each other than either is to JavaScript, and they both make JavaScript a lot more DRY and pleasant to deal with. But let's look at the differences:

[Kaffeine](http://weepy.github.com/kaffeine/) pros:

* Kaffeine has the major benefit of maintaining line numbers. With CoffeeScript, any error messages require a little thinking in order to track down the bug. Sometimes I even have to manually compile the CoffeeScript to track down the errant code (some of the various ways I'm using CoffeeScript only ever serve the JS, or keep it in memory, rather than ever saving it).
* Retains ternaries, which, being symbolic, are more to my liking than the "if then else" CoffeeScript idioms. (I like symbols for code structures because what words remain are those that matter, i.e. those related to business and application concepts.)
* Has a number of nice "coding in the small" idioms which aren't present in CoffeeScript, especially the [pipe](http://weepy.github.com/kaffeine/docs/operators.html) and [async](http://weepy.github.com/kaffeine/docs/unwrapping_async_calls.html). The latter lets you create a traditional "sleep 1000" on its own line, giving the illusion of synchrony.
* Doesn't impose Python-like significant whitespace. Actually, I've come to like this about CoffeeScript (see below), but there's certainly a learning curve until you get how to handle the various situations, which doesn't need to happen with Kaffeine.
* Truly JS++. The Kaffeine compiler will compile a regular JavaScript file just fine. With CoffeeScript, although the language aspires to be "it's just JavaScript", standard features like "function" keyword are simply not part of the syntax.

[CoffeeScript](http://jashkenas.github.com/coffee-script/) pros:

* There's one extremely compelling reason to choose CoffeeScript right now, above all other dialects: The ecosystem. There's exponentially more docs ([the core docs](http://jashkenas.github.com/coffee-script/) themselves are great), more existing code, and more tools in CoffeeScript, than any other dialect. (Just as the ecosystem of JavaScript is in turn exponentially bigger than that of CoffeeScript.) Don't get me wrong. It's great that other dialects like Kaffeine are out there pushing the barrier, and even the less JavaScripty tools like ClojureScript and Dart which treat JavaScript more like a virtual machine. And because they all compile down to JavaScript, you can use them today. **But** if you want to ship code fast, CoffeeScript is the sweet spot right now: The benefits you'd want in a "JavaScript++", with best support and minimal effort to integrate it into projects. There are already several CoffeeScript books in the making, for example. StackOverflow registers 600+ questions about CoffeeScript, while other dialects are in the single or low double digits. (And 130K questions about JavaScript, to prove my point about CoffeeScript still being a minnow in the big JS sea!) There are also an increasing array of tools where CoffeeScript support comes out of the box, e.g. [connect-assets](https://github.com/TrevorBurnham/connect-assets).
* For a related reason, CoffeeScript may be the most future-proof dialect out there. Though we can expect JS.Next to learn from all the dialects, it's clear Brendan Eich is [paying close attention](http://blip.tv/jsconf/jsconf2011-jeremy-ashkenas-5258082) to CS:
<iframe src="http://blip.tv/play/g_MngsD3RgI.html" width="450" height="320" frameborder="0" allowfullscreen></iframe><embed type="application/x-shockwave-flash" src="http://a.blip.tv/api.swf#g_MngsD3RgI" style="display:none"></embed>

* The syntax is best described as **relaxing**! (With apololgies to CouchDB.) I initially balked at the significant whitespace, but now I appreciate its ability to wipe out curly braces and parentheses. It's just nice to define hash literals without commas and braces, for example.
* Operators like "isnt" and "unless" make the code much more literate. Why add extra baggage? Because to a computer "5==count" is the same as "count==5", but to a human, there's always a context which makes one more natural. See [Yoda Conditions](http://stackoverflow.com/questions/2349378/new-programming-jargon-you-coined/2430307#2430307). These kinds of expressions help avoid double negatives too.
* Class construct, which like everything, "de-sugars" to regular JavaScript.
* There's [a reverse compiler](http://js2coffee.org/). Nice if you want to fork an existing JS library or code example.

I'm still not done yet. While these are "just" dialects of JavaScript, each has a sufficiently large feature set that it takes a while to get the hang of everything, when you're using them in real-world projects. So I'm still jumping back and forth between my code and the doco to make sure I'm getting full benefit of both.

A few caveats about JavaScript dialects:

* As I've already pointed out, JavaScript is still vastly more standard than any dialect. While Dart may come to Chrome in the future, and various features will morph into JS.Next, you're always going to be doing more tool integration and working with less docs. If releasing open source, you'll want to distribute the JS or at least make it easy for someone to generate it. What's good though is you don't have to learn something completely different, so it doesn't become a maintenance issue. You could easily hire a JS developer to maintain a CS app, they'll be up and running in a few.
* All create extra overhead in terms of tooling. Whether you're dealing with a browser or Node, both of those deal in the currency of JavaScript, and some conversion must take place.
*  There are many situations where you still have to use plain old JavaScript. For example, working with legacy code or other people's JavaScript. Writing inline script tags or dynamic code which will be eval'd in the browser (unless you also want users to download the CS compiler). You'll need to get used to switching between the two, and that's painful because once you start working with them, trust me, you WILL NOT want to go back. (This has been true for Jade vs HTML and Stylus vs CSS as well.) So I'm often having to consciously ask myself what I'm coding in right now.