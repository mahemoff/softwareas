---
id: 232
title: 8 New Ajax Patterns (Diagnosis and Testing)
date: 2005-11-06T14:29:40+00:00
author: admin
layout: post
guid: http://www.softwareas.com/8-new-ajax-patterns-diagnosis-and-testing
permalink: /8-new-ajax-patterns-diagnosis-and-testing/
categories:
  - Links
  - SoftwareDev
tags:
  - Agile
  - AjaxPatterns
  - DHTML
  - JsUnit
  - JUnit
  - Links
  - Logging
  - QA
  - Rhino
  - Software
  - Testing
  - Web
  - Web 2.0
---
Cool! <strong>The Best Practices/Processes Patterns are now complete.</strong> They are the final eight Ajax Patterns for now - "final" in the sense of "the list is not yet finalised". The patterns had been sitting there unattended for about four months now.

More details on the new patterns later, but here's a quick summary ...

First, there's a new demo - <strong>the Ajax Patterns Reader</strong> - the best version to try is at [http://ajaxify.com/run/reader/logging/realService/](http://ajaxify.com/run/reader/logging/realService/). <strong>The reader grabs the AjaxPatterns.org content and presents them Ajax-style</strong>. You actually queue up patterns in a playlist and click "Next" to "play" them. Yeah, a bit contrived, but it helped illustrate quite a few patterns! If I have time, I'd like to enhance it into a proper reader, and also offer an easy interface to leave feedback, which would be automatically appended to the wiki's Discussion tab for that pattern.

BTW [This further refactoring of the Ajax Patterns Reader](http://ajaxify.com/run/reader/logging/realService/ghost) illustrates the [Scriptaculous GhostTrain tool](http://wiki.script.aculo.us/scriptaculous/show/GhostTrain). If you haven't seen GhostTrain, have a look - the Javascript will track your activity and build up a test case dynamically (covered in the new [System Test pattern](http://ajaxify.com/run/System_Test)). All within the browser. I've been in contact with the developers (Thomas and Jon), and discovered it's still proof-of-concept, but if they can tie it all together, it will be an excellent way to create a system/functional test. 

Next, there's four patterns on diagnosis:

<strong>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Logging" title="Logging">Logging</a>
Instrument your Javascript with log messages.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Debugging"
title="Debugging">Debugging</a> Diagnose problems with a Javascript
debugger.</span>
</li><li> <span class="full"><a href='http://ajaxpatterns.org/DOM_Inspection'" title="DOM
Inspection">DOM Inspection</a> Use a DOM Inspection Tool to explore the dynamic
DOM state.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Traffic_Sniffing" title="Traffic
Sniffing">Traffic Sniffing</a> Diagnose problems by sniffing <a href="/wiki/index.php?title=Web_Remoting&amp;action=edit" class="new"
title="Web Remoting">Web Remoting</a> traffic.</span>
</li></ul>
</strong>

And finally, four patterns on <strong>testing</strong>:

<strong>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Simulation_Service" title="Simulation
Service">Simulation Service</a> Develop the browser application against "fake"
web services that simulate the actual services used in production.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Browser-Side_Test" title="Browser-Side
Test">Browser-Side Test</a> Create automated tests of browser-side Javascript
components.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Service_Test" title="Service
Test">Service Test</a> Build up automated tests of web services, using HTTP
clients to interact with the server as the browser normally would.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/System_Test" title="System Test">System
Test</a> Build automated tests to simulate user behaviour and verify the
results.</span>
</li></ul>
</strong>

