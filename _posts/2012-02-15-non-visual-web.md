---
id: 1489
title: The Non-Visual Web
date: 2012-02-15T22:59:19+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1489
permalink: /non-visual-web/
enclosure:
  - |
    http://audio.5by5.tv/broadcasts/webahead/2012/webahead-016.mp3
    46809216
    audio/mpeg
    
categories:
  - SoftwareDev
tags:
  - html5
  - Mobile Web
  - Podcasting
  - Web
---
###Looking Forward

7 years on from Ajax, we have our JavaScript-fu down and the APIs we could ever have dreamt of are baked into the desktop browsers of note. So what's next for the web? The latest 5x5 podcast with Jason Grigsby is illuminating on future trends (as well as being a must-listen for all its practical advice):

<audio controls='controls' src='http://audio.5by5.tv/broadcasts/webahead/2012/webahead-016.mp3' />

[Episode Homepage](http://5by5.tv/webahead/16-mobile-capabilities-with-jason-grigsby)

Here I want to outline a few specific features which will challenge the boundaries of the web as we know it. And then I'll explain how the web community can meet those challenges.

###Tip of the Iceberg

In 2009, I gave a talk at London Web Standards on eight features of HTML5 you won't see, features such as offline storage, geolocation, and history API.

<a href='http://www.steveworkman.com/html5-2/2010/8-html5-features-you-havent-seen-before-at-lwsdeep/'><img width='300' src='http://www.steveworkman.com/wp-content/uploads/2010/09/8-html5-features.png' /></a>

That's the tip of the iceberg of the tip of the iceberg. An example in this podcast is walking down the street and having your phone's navigation system vibrate once if you should turn left, twice if you turn right. Another example mentioned in the podcast is a <a href='http://webinos.org/blog/2012/02/08/webinos-demo-series-1-vehicle-api/'>JavaScript vehicle API</a>! <tt>webinos.vehicle.addEventListener (webinos.vehicle.NavigationEvent.DESTINATION_REACHED, handleDestinations, false);</tt> Checking fuel level, engine condition, etc. via a high-level API. And of course, there's the whole medium of sound...this post was kicked off by a podcast after all!

**The web has traditionally been a visual medium. As Jen Simmons observes here, even when it's not visual, we use the word "Screen Reader" to emphasise its visual foundations.** While it's moved from text to images to fancy graphics and multimedia, those things are still visual elements on the page. Yet all of the above are not about elements on the page. <a href='http://designmind.frogdesign.com/blog/the-coming-zombie-apocalypse-small-cheap-devices-will-disrupt-our-old-school-ux-assumptions.htm'>That's where technology is headed</a>. So is it even sensible to handle these things through the web?

###Model-View Separation

On a technical level, what makes the web incredibly powerful is the DOM concept. DOM is sync'd to UI. Update the DOM and it changes the user-interface. Change the UI and the DOM updates. The programmer doesn't have to facilitate this bidirectional sync; it just happens.

Really, on a technical level, this is an incredibly important and overlooked aspect of HTML5. Too many HTML5 APIs are pure JavaScript functions and ignore the DOM altogether. For the web to thrive, vehicle APIs should not just be <tt>webinos.vehicle.addEventListener</tt>. The <tt>vehicle</tt> itself should be part of the DOM. If that sounds too domain-specific, that's okay, because look at the work of [Web Components](https://plus.google.com/103330502635338602217).  These guys are bringing about a world where anyone, or any community, can create a first-class &lt;x-vehicle&gt; element with its own look-and-feel.

###Open Standards

Of course, at a higher level, the web is about open standards. That's really what sets it apart from iOS, Android, and .Net. There's no single vendor in charge. Something like the Java Virtual Machine comes close, but the web stack stands out as a more balanced control system. If there are to be standards for things like vehicle APIs, the web is attractive as the best stab at a neutral ground with real developer buy-in.

<a href='http://thewebisagreement.com/'><img src='http://picupper.com/2012/02/15/1805709102_4fc795431b.jpg'></a>

For this reason, the web can successfully move beyond the visual medium without losing what makes it the web in the first place.