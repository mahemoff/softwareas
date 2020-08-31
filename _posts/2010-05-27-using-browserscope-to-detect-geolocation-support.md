---
id: 911
title: Using BrowserScope to Detect Geolocation Support
date: 2010-05-27T22:32:28+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=911
permalink: /using-browserscope-to-detect-geolocation-support/
dsq_thread_id:
  - "375574742"
categories:
  - SoftwareDev
tags:
  - Browserscope
  - Geolocation
  - html5
  - Javascript
  - Testing
  - Web
---
<h4>About Browserscope</h4>

<a href="http://browserscope.org">Browserscope</a> is a very cool tool coming out of Steve Souders' performance efforts and being developed by Steve along with Lindsey Simon. It's part of a trend towards crowdsourcing browser info, in similar vein to <a href="http://testswarm.com">TestSwarm</a>, for testing specific code, and along the lines of what I did with <a href="http://webwait.com">WebWait</a>, which is to support multiple people benchmarking a website at once. (Though I've not set up reporting on it - one day...)

So anyway, Browserscope began life as a way to benchmark just performance, but is now a general-purpose tool for crowdsourcing tests about anything browsers do, e.g. checking for security vulnerabilities is one vital application. HTML5 does not miss out - <a href="http://html5test.com">HTML5Test.com</a> has been ported over too - see <a href="http://beta.html5test.com">beta.html5test.com</a>.

<h4>Geolocation Test</h4>

I decided to make my own test recently, to see what extent Geolocation is being supported by the browsers. Run the test against your browser here (it will upload only information about whether geo is supported, not your actual geolocation data):

<a href="http://test.mahemoff.com/geo.html">http://test.mahemoff.com/geo.html</a>

The results so far indicate browsers either don't support it, or support accuracy+lat+lon. I was hoping to see at least direction, and would <3 to see altitude! But it will have to wait.

<h4>How to Make your Own Browserscope Test</h4>

If you ever wanted to know how every browser under the sun handles a particular something, Browserscope is your new hotness. It makes it trivial. Register with Browserscope to get the boilerplate code. Then you just write an app that does the exercises and builds up a hashmap of the info you want to collect, and BAM, submit it. The hashmap should have values between 1 and 1000. Do that, and you'll end up with a nice summary page showing your test results aggregated across all browsers that ran them.

The submission is taken care of by some boilerplate code - it uses on-demand Javascript to pass the data back to the third-party BrowserScope domain (you host the test yourself). Aside from writing the actual test and promoting its location, the only thing you have to do is make a nice UI to show the users what you just did, and perhaps get their consent before uploading. I think those are actually two things Browserscope could automate too, at least providing a nice default UI which test creators can customise.