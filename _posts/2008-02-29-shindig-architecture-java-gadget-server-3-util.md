---
id: 431
title: 'Shindig Architecture: Java gadget Server 3 &#8211; Util'
date: 2008-02-29T18:11:54+00:00
author: admin
layout: post
guid: http://softwareas.com/shindig-architecture-java-gadget-server-3-util
permalink: /shindig-architecture-java-gadget-server-3-util/
dsq_thread_id:
  - "393949303"
categories:
  - Links
  - SoftwareDev
---
More raw Shindig notes. This time, looking at org.apache.shindig.util. See <a href="http://softwareas.com/tag/shindigging">Shindigging tag</a>. This is just a quickie for completeness sake as it's a few generic util classes. This post completes the listing of all Java classes in the Shindig architecture at this time.<br />

Check - Runs some standard assertions (empty null etc).

InputStreamConsumer - Input stream -> String

ResourceLoader - Loads some files within a path. Will trawl through path and also open up any JARs.