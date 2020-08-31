---
id: 870
title: 'Audio/Video Tag: Don&#8217;t Forget to load() before you play()'
date: 2010-04-30T03:33:29+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=870
permalink: /audiovideo-tag-dont-forget-to-load-before-you-play/
dsq_thread_id:
  - "375337975"
categories:
  - SoftwareDev
tags:
  - audio
  - html5
  - Javascript
  - Video
---
<img src="http://picupper.com/2010/04/29/music.jpg" />

This is a gotcha that will catch a lot of people out because it goes against the expectation that you just change an image's appearance by setting its "src", done. And also, it's a deviation from the more general convention that you change DOM properties declaratively to make stuff happen. Probably for good reason, given the temporal nature of audio and video playback, but just beware it's a different model.

<strong>Bottom line is - load() between changing src and play()ing</strong>:

[javascript]
function play(url) {
  var audio = document.querySelector("audio");
  audio.src = url;
  audio.load(); // !HUL|_O! PAY ATTENTI0N!
  audio.play();
}
[/javascript]

A lot of online sources talk about play() and omit to mention this vital fact, because they're only play()ing a single track...and the first track works fine. This is an oddity - you can just call play() the first time and it will automatically load. This happens whether you set "src" in the initial HTML's "audio" tag or whether you set it programatically. I did some <a href="http://jsfiddle.net/QkGEr/3/">fiddling</a> and it looks like the behaviour is the same in Chrome and Firefox. It's like the track is auto-load()ed the first time you set its source. (And note that <a href="http://hacks.mozilla.org/2009/12/autobuffering-video-in-firefox/">Firefox doesn't auto-buffer</a> so that's nothing to do with it.)

<a href="http://www.devx.com/webdev/Article/43324/1954">devx</a> has you covered on this topic, and points out the subtle issues which you would need to look at for a quality production:

<blockquote>
However, media by its very nature is a time-spanning process. You're working with both the need to load and cache audio and video files and the network connection, which itself can prove to be a challenge that's usually not a factor for most non-temporal resources. For these reasons, when dealing with video and audio on the web, if you want to take control of the process in any way, you have to work asynchronously, tying into the various events that are passed back to the client from the media-serving website. Table 4 (taken directly from the HTML 5 documentation) provides a full listing of the various events and when they are dispatched.
...
Of all the events in Table 4, perhaps the most useful are the canplay and canplaythrough events. The first, canplay, will fire when enough data has been loaded for the video player to start actually rendering content constructively, even if not all of the data has been loaded. The canplaythrough event, on the other hand, will fire when the data has essentially completely loaded into the browser's buffer, making it possible to play the video all the way through without the need to pause and retrieve more content.
</blockquote>