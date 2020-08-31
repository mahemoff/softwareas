---
id: 527
title: '&#8220;Moving There&#8221;: Property Listings Mashup (Rewired State)'
date: 2009-03-24T08:45:04+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=524
permalink: /moving-there-property-listings-mashup-rewired-state/
dsq_thread_id:
  - "400806581"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Government
  - Mashup
  - Rewired State
  - Web 2.0
---
<embed src="http://blip.tv/play/AfWNfJWQbA" type="application/x-shockwave-flash" width="380" height="300" allowscriptaccess="always" allowfullscreen="true"></embed>

I recently attended <a href="http://rewiredstate.org">Rewired State</a> with several fellow Osmosofties. Our group (<a href="http://simonmcmanus.com">Simon</a>, <a href="http://fnd.lewcid.org">Fred</a>, <a href="http://jermolene.com">Jeremy</a>, <a href="http://blog.iclutton.com/">Robbie</a> and myself) developed a little mashup called Moving There (and a couple of other things not described here).

After the demos, our mashup was mentioned by a representative from DirectGov as one of several projects they'd like to work with, perhaps to sponsor further work.

The idea was to overlay government-related data on property listings sites. I've been moving house right now, so this is very much an itch which I'd very much like to scratch.

Typical properties listings sites like <a href="http://rightmove.co.uk">RightMove</a> show a list of properties matching your search criteria (shown below).

<img style="width: 380px;"  src="http://img.skitch.com/20090323-nk2xur4xeuswtdtehym6ij6j36.jpg" />

There's a lot of things they don't show you too, like upcoming building works, local schools, crime stats, vandalism. All these things are available in one form or another on websites, some operated by the  government and others by third parties.

<a href="http://project.mahemoff.com/movingthere/movingthere.html"><img style="width: 380px;" src="http://img.skitch.com/20090323-fqgmkpy2ucqpsabgebegwhjxwc.jpg" /></a>

One part of our work involved taking in a postcode and producing useful info about it, so we came up with a little library for that. We also made some attempt to normalise these metrics, so we came up with a "coolness factor" between 0 and 1. This is very crude, but we feel it's useful when comparing stats to say "schools have a coolness factor of 0.3 and crime prevention is 0.6" rather than "schools have an average pass rate of 48% and there are 142 crimes per week". In other words, a standard coolness factor measure goes some way towards helping you compare apples with oranges.

<a href="http://project.mahemoff.com/movingthere/testgrabber.html"><img style="http://img.skitch.com/20090324-mmxp46hq8ch33crafy7nw6yu51.jpg" /></a>

But the real product concerned itself with mashing up a properties listing site. After entering a location, you get back listings as well as charts showing the "coolness" factor according to the various stats. Well, that's the theory; in this case, it's just one stat (fixmystreet local incidents, e.g. vandalism) per property. And the UI isn't particularly slick either! I'm just presenting where we got to when the time ran out on the day!

<a href="http://project.mahemoff.com/movingthere/search.html"><img style="width: 380px;" src="http://img.skitch.com/20090323-gdr8dw6uf5jpf9wjpctpafhp9h.jpg" /></a>

A few notes on the technology. We made use of <a href="http://jquery.com">JQuery</a> for the usual infrastructural stuff. We used <a href="http://code.google.com/apis/maps/documentation/services.html">Google's geo-coding API</a> to map street name and suburbs into a postcode. The postcode info demo and the final mashup are actually a file-based web app, i.e. it runs off a file:// URI. We debated several models for the mashup's architecture; in retrospect, we spent a lot of time re-building the property search's UI and it might have been better to go with a Greasemonkey overlay, at least for proof-of-concept.