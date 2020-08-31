---
id: 1950
title: How HTTP client libraries should support redirects
date: 2014-04-16T10:52:00+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1950
permalink: /how-http-client-libraries-should-support-redirects/
categories:
  - SoftwareDev
---
<a href="http://imgur.com/B7wFgLd"><img src="http://i.imgur.com/B7wFgLd.jpg" title="Hosted by imgur.com" /></a>

I don't think I've ever come across an HTTP library (and I'm including XMLHttpRequest here) that covers all bases on redirects. In the hope of pushing the field forward, here is my wishlist. I'm limiting this to just GETs as it gets even more complicated with the mutating actions. (Several browsers do XMLHttpRequest wrong in the case of POST redirects.)

* Follow redirects by default (it's the most typical need after all), but provide an option to turn that off.
* Allow a limit on redirect-following recursion, to prevent too much redirecting [1].
* Prevent infinite redirect cycles. Which arise due to misconfiguration or malicious denial-of-service efforts [1].
* Report back the chain of redirection, with corresponding status codes (ie was it permanent?).

It's really the last point that's universally missing. For services like [Player FM](https://player.fm) which need to retain a record of permanent redirects, it's necessary. The lack of this features means having to write custom code to follows redirects. Which isn't a giant burden, but it's error-prone, a pain to test, and has to be done for every kind of resource.

1. The recursion limit requirement has the side benefit of preventing infinite redirect cycles, so that alone may be adequate for a library. But it's worth treating a separate requirement because: (a) it can be even more optimal if handled separately (ie it can terminate even before the limit is reached); (b) if the library does rely on some limit to prevent infinite recurison, the library should nevertheless enforce some maximum, e.g. 100, and also set some sane default, e.g. 5.

Photo Credit: <a href="http://www.flickr.com/photos/10413717@N08/5735124662/">Smabs Sputzer</a> via <a href="http://compfight.com">Compfight</a> <a href="https://creativecommons.org/licenses/by/2.0/">cc</a>