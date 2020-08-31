---
id: 842
title: WebWait Updated
date: 2010-04-14T01:59:36+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=842
permalink: /webwait-updated/
dsq_thread_id:
  - "375574697"
categories:
  - SoftwareDev
tags:
  - Project
  - Web
  - WebWait
---
One of the projects I wanted to work on in my time off was <a href="http://webwait.com">WebWait</a>.

It finally does what I wanted it to do all along: Permanently record benchmarks. You can get a unique URL for each benchmarking session you run by hitting Save. Funny - WebWait was running as a Rails app for several years, but was always a pure browser-side client until I finally completed this. (Ultimately, I didn't use Rails anyway - see below.)

<a href="http://webwait.com/1"><img src="http://farm5.static.flickr.com/4068/4519047329_58666b6d67_o.jpg" /></a>

Some other enhancements too ...

* Bar charts (using the Google Charts API):

<img src="http://farm5.static.flickr.com/4028/4519684544_3354338700.jpg" />

* Expanded dashboard, showing a box for each site you've trialled. (Previously, there was only one box ever shown, the latest one. Since people like taking screenshots of these, I figured it would be cool to include multiple boxes.)

<img src="http://farm5.static.flickr.com/4008/4519683900_259ed0cd8e_o.jpg" />

* There is also <a href="http://webwait.com/1.json">a JSON view</a> of the trials that were recorded.

It would be cool to expand it further, for example allowing pages to be cross-linked when they benchmark the same trial. But I'll leave it here and see where demand takes it.

The new WebWait server is powered by the incredibly productive trio of Ruby, Sinatra, and TokyoCabinet. On the browser, it's still jQuery, with the <a href="http://datatables.net/">DataTables plugin</a> and my own <a href="http://github.com/mahemoff/jQuery-iFrame">jQuery iFrame plugin</a>.
Hosted on SliceHost (where I have now <a href="http://mini.softwareas.com/techscribbles-ubuntu-sysadmin-tasks-for-webse">happily migrated many things</a>.)