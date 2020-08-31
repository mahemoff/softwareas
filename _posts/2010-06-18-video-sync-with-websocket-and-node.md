---
id: 918
title: Video Sync with WebSocket and Node
date: 2010-06-18T17:45:13+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=918
permalink: /video-sync-with-websocket-and-node/
dsq_thread_id:
  - "375500777"
categories:
  - SoftwareDev
tags:
  - html5
  - Javascript
  - Video
  - WebSocket
---
<object width="425" height="344"><param name="movie" value="http://www.youtube.com/v/r90ti4MbecM&hl=en&fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/r90ti4MbecM&hl=en&fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="344"></embed></object>

[Update 2015 - This was made on a very early version of NodeJS and may not work anymore; if you are looking for support to run this, please ask on StackOverflow.]

Wanting to explore WebSocket, I made a demo that syncs videos for all users looking at the page (<a href="http://gist.github.com/443933">See the Code</a>). Any user can "take control", so that the other videos will follow the controller's video. Writing it was a cinch with the Javascript WebSocket API in the client, and the very straightforward <a href="http://github.com/miksago/node-websocket-server">Node WebSocket Server</a> powering the server.

Note it's just a simple demo - there's no security model here and there's a very simple sync mechanism: When a "slave" client receives the latest duration, it adds a second to account for lag, and moves the video iff there's a 5-second discrepancy.

How does a WebSocket client look? Well, it looks a lot simpler than a traditional Comet client. Initiate the connection with "new WebSocket":

[javascript]
  var conn;
  $_("#join").onclick = function() {
    conn = new WebSocket("ws://localhost:8000/test");
[/javascript]

Upload a message to the server with send():
[javascript]
    video.addEventListener("timeupdate", function() {
      if (iAmControlling()) conn.send(video.currentTime);
    }, true);
[/javascript]

Receive a message from the server with conn.onmessage():
[javascript]
  conn.onmessage = function (ev) {
    if (matches = ev.data.match(/^pause (.+)$/)) {
      video.pause();
      video.currentTime = matches[1];
    }
    ...
  }
[/javascript]

And when it's time to draw the curtains, close the connection with another one-liner:
[javascript]
  $_("#leave").onclick = function() {
      conn.close();
      ...
    };
[/javascript]

The server is also rather tiny. It mostly just broadcasts (sends to all clients) any incoming message and it's up to the clients to deal with it. Which is why I say there's no real security model here.

As you can see in the above snippets, "video" plays an excellent cameo role here, with its <a href="http://diveintohtml5.org/video.html">equally simple API</a>. One downside, which others <a href="http://www.systemerror.co.uk/2010/05/06/html5-video-real-world/">have mentioned too</a>, is the lack of styling in the default video controls. It's great the API supports automatic controls, but it's unfortunate there's no CSS manipulation. In this case, the "slave" browsers should be able to see the time, but not have the ability to change the progress. I hope this changes in the future, because the API is otherwise very powerful without compromising simplicity. Until then, <a href="http://www.longtailvideo.com/support/forums/jw-player/feature-suggestions/10383/html5-version-of-jw-player">libraries</a> will arise to fill the gap.

The demo works in both Chrome and Safari (and they play nice simultaneously).