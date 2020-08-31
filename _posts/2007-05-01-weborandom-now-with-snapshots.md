---
id: 373
title: 'Weborandom &#8211; Now With Snapshots'
date: 2007-05-01T23:40:50+00:00
author: admin
layout: post
guid: http://www.softwareas.com/weborandom-now-with-snapshots
permalink: /weborandom-now-with-snapshots/
dsq_thread_id:
  - "375573275"
categories:
  - SoftwareDev
tags:
  - Links
  - Snap
  - Snapshots
  - Weborandom
---
<a href="http://weborandom.com"><img width="380" height="300" src="http://img91.imageshack.us/img91/254/webosnapsnu3.png"/></a>

This mashup was just obvious. You've probably seen these snap.com website previews that hover over links on <a htef="http://techcrunch.com">TechCrunch</a> and various other sites. Can be useful and can be, well, a bit annoying, depending on the site in question. For Weborandom, though, there was no question. It just made eternal sense and I kept imagining it was there, so it was high time I added it in. Admittedly, Weborandom already provides a preview, so this is a kind of preview for a preview. Works for me anyway. With thanks to <a href="http://snap.com">snap.com</a> for providing their easy-to-integrate API, it's now live.

<a href="http://weborandom.com">Go visit the new, new, Snapshots (TM)-enabled, Weborandom.com!!!</a>

The main challenge was to make the previews refresh dynamically, which was achieved with a little <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a> magic:

[javascript]
function refreshSnapshots() {
  var head = document.getElementsByTagName("head")[0];
  var script = $("snapshotScript");
  if (script) { head.removeChild(script); }
  script = document.createElement("script");
  script.id = 'snapshotScript';
  script.type = 'text/javascript';
  script.src = "http://shots.snap.com/snap_shots.js?ap=1&amp;key=d2e3ec72c47f90dc1ccf4c25de818ed2&amp;sb=0&amp;th=silver&amp;cl=0&amp;si=0&amp;po=0&amp;df=0&amp;oi=0&amp;link_icon=on&amp;shots_trigger=icon&amp;size=large&amp;lang=en-us&amp;domain=weborandom.com";
  head.appendChild(script)
}
[/javascript]

I daresay the next installment will be the big one: search. It was originally intended to do that, but mysql fulltext queries crawl with several million records. I'll need to experiment with ferret and friends.