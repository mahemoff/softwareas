---
id: 1080
title: 'WebWait Upgrade: Deletion, Quick Entry of Multiple Sites'
date: 2011-01-15T21:12:22+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1080
permalink: /webwait-upgrade-deletion-quick-entry-of-multiple-sites/
dsq_thread_id:
  - "378229254"
categories:
  - SoftwareDev
tags:
  - Javascript
  - Project
  - WebWait
---
<a href="http://webwait.com"><img src="http://farm6.static.flickr.com/5166/5358166132_b1bb0883ce_o.jpg" /></a>

I made a couple of upgrades to WebWait this week.

First, you can now delete entries. This is useful for curating a set of results, since you can save a result set for others to try out, or for later analysis and comparison. If I get requests, I may also allow users to re-order the results for that reason too. You can only delete a trial when it is complete, i.e. when all calls to it have been made. This is not ideal, but would require significant rework. Again, I'll respond to feedback on this one.

Second, you can now enter multiple URLs in the input field, separating them by space. I received a request from a Dzmitry Markovich, who wanted to time hundreds of websites at once, and figured I should support it. It's an undocumented feature intended for advanced users, as I don't have time to think about how to integrate it into the UI without compromising the simplicity of the design (e.g. with a text area; I should at least mention the feature in the FAQ, which is now ancient.) In the case of someone wanting to enter dozens or hundreds of websites, they need to cut-and-paste into the input field.

Funnily enough, both of these features had previously existed, but were removed when I overhauled the architecture to make way for the <a href="http://softwareas.com/webwait-updated">benchmark saving feature</a>. The new architecture, being based on semantic events, made the deletion feature rather easy. The multiple-URL feature was also quite straightforward, as it would be with any architecture.

This is the latest of <a href="http://softwareas.com/tag/webwait">four updates</a> in WebWait's lifetime of as many years. Slowly but surely :).