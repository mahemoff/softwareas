---
id: 406
title: Screencasts with Audio on Wink
date: 2007-11-07T10:05:51+00:00
author: admin
layout: post
guid: http://www.softwareas.com/screencasts-with-audio-on-wink
permalink: /screencasts-with-audio-on-wink/
dsq_thread_id:
  - "375330567"
categories:
  - SoftwareDev
tags:
  - Screencast
  - Video
  - Wink
---
I'm at a workshop on widgets. At a lot of workshops, people build some code, demo it, and then go away and no-one can see it running again. In an ideal world, we'd keep the apps running forever, but that relies on a complex tangle of internal and external services remaining online and staying in the same form. For example, will <a href="http://twitter.com/oauth">Twitter's experimental OAuth</a> have the same interface in six months time as it does today? In an experimental workshop involving mashups, there are bound to be numerous calls to services like that. The best way to preserve the work is not to keep the apps running, but to capture screencasts where the developers can explain the underlying concepts.

On Mac, I use <a href="www.shinywhitebox.com/home/home.html ">iShowU</a> for screencasts (like the <a href="www.youtube.com/watch?v=bZ9WhpQhv8g">Web-O-Random</a> screencast I did a while ago). For Windows and Linux, though, there's the possibility of Wink, which is nice as it's (a) free; (b) capable of producing SWF files directly (Flash movies which can be embedded in a web page like YouTube). Last tried Wink two years ago to make some AjaxPatterns screencasts that never happened. (It's funny to think that at the time, I was bothered about how to host and serve these files, a few MB each. Now I'd just store them on Dreamhost at 1+TB/month for about $20.)  At the time, Wink didn't handle sound, so you had to go through contortions to get an SWF movie containing the screencast with audio. Now it does, but it turns out to be not brilliant. When I tried to record with the "audio" option checked, the audio ended up being broken - 1 second on, 1 second off. Would be indicative of a buffering issue, but there's plenty of memory available.

So here's what I discovered, which actually works (using Wink 2.0). Instead of simultaneous audio and video, you can record audio over a single - frozen - frame. i.e. the frame will be frozen while you say your thing. It's not Tarantino, but good enough for an explanatory screencast.
<ol>
  <li> Start a new project, with audio option <b>not</b> checked.</li>
  <li> Record the interaction without audio (Shift-Pause to start, Alt-Pause to stop). Don't slow down on critical events as you can easily add delays during editing.</li>
  <li> Once you're done recording, Wink will show a reel of all frames on the bottom of the screen.</li>
  <li> Click on a frame showing a critical event. On the right of the screen, there's a dialog showing properties for this frame.</li>
  <li> Click on "+" audio button, which will produce a recorder. You can now record some audio which will sound out while showing the frame. <em>The frame is automatically paused for as long as the audio you record.</a>
  <li>Now do <tt>Project Menu|Render</tt> and then <tt>Project Menu|View Rendered Output</tt> to see your video and hear your narration.
</ol>

(I'm aware this is a plain-text post, explaining how to use software without screenshots or screencasts. Isn't it ironic?)
