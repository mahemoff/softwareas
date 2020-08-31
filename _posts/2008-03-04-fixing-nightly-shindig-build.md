---
id: 432
title: Fixing nightly Shindig build
date: 2008-03-04T02:32:57+00:00
author: admin
layout: post
guid: http://softwareas.com/fixing-nightly-shindig-build
permalink: /fixing-nightly-shindig-build/
dsq_thread_id:
  - "386119505"
categories:
  - SoftwareDev
tags:
  - Shindig
---
<i>Update: Instead of the following, which assumes you're running containers off the filesystem, you should really run them off the web server. So the recommended way to run Shindig's sample container is "jetty:run-war" (not documented in the README, but my alert colleague located it on the mailing list). Then point to http://localhost:8080/gadgets/files/container/sample2.html.</i>

I checked out the latest version today (628639) and FWIW these are the changes I made to the sample container to get it running (same as a week or so earlier):

Add libraries to HTML (e.g. sample1.html):
[html]
<script type="text/javascript" src="../../features/core/core.js?c=1"></script>
<script type="text/javascript" src="../../features/core/util.js?c=1"></script>
[/html]

Edit rpc path (e.g. sample1.html):
[html]
<script type="text/javascript" src="../../features/rpc/rpc.js?c=1"></script>
[/html]

Edit default server base in gadgets.js 
[javascript]
// assumes you're running jetty gadget server locally.
this.serverBase_ = "http://localhost:8080/gadgets/";
// or if you're too lazy ;) to serve them yourself, Google is your friend ...
this.serverBase_ = "http://www.gmodules.com/ig/";
[/javascript]