---
id: 396
title: Drag a custom window with Adobe Air
date: 2007-07-29T17:07:08+00:00
author: admin
layout: post
guid: http://www.softwareas.com/drag-a-custom-window-with-adobe-air
permalink: /drag-a-custom-window-with-adobe-air/
dsq_thread_id:
  - "375573354"
categories:
  - SoftwareDev
tags:
  - Air
  - Apollo
  - Links
---
Quick tip. Been playing with Adobe Air recently and was trying to let the user drag a <tt>"systemChrome="none" transparent="true"</tt> around. The <a href="http://ajaxian.com/archives/adobe-air-free-book-download">definitive Air reference</a> has an example that shows how to close and minimize, but not how to move it. And all the examples I could find are <a href="http://technoracle.blogspot.com/2007/07/air-apple-shaped-application.html#links">Flash-based</a> rather than the HTML/JS/Ajax approach I'm taking (along with some forum posters who were as confused as I was). Based on the Flash examples and the close/minimise pattern, it turned out to be this simple:

[javascript]
     document.body.onmousedown =
        function() { window.htmlControl.stage.window.startMove(); }
[/javascript]

