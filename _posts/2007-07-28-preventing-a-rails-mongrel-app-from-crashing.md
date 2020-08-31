---
id: 393
title: Preventing a Rails (Mongrel App) from Crashing
date: 2007-07-28T03:53:11+00:00
author: admin
layout: post
guid: http://www.softwareas.com/preventing-a-rails-mongrel-app-from-crashing
permalink: /preventing-a-rails-mongrel-app-from-crashing/
dsq_thread_id:
  - "375573349"
categories:
  - SoftwareDev
tags:
  - Mongrel
  - Monit
  - MySQL
  - Rails
  - Ruby
---
<a href="http://www.costumedogs.com/archives/if-batman-has-bat-dog-what-does-bat-dog-have"><img src="http://picupper.com/2007/07/27/batdog.jpg" width="220" height="300"/></a>

I've had a Rails website which works fine for about 12-18 hours, then starts giving out intermittent 500 errors because the <a href="http://mongrel.rubyforge.org/">mongrels</a> die.

After searching around, I ended up fixing it on two levels.

<strong>(a) Direct solution - Fix MySQL config</strong> One reason Mongrels die is MySQL connections not timing out, leading to starvation. Apparently there's a bug here which means you have to set "ActiveRecord::Base.verification_timeout = 14400" in environment.rb, the figure must be less than MySQL's interactive timeout, which is 8 hours (28800 secs, so this is half of that). But <a href="http://groups.google.com/group/activemessaging-discuss/browse_thread/thread/7cbbcd761fcb0fd8">as this thread points out</a>, it doesn't seem like that will achieve a whole lot on its own, so there's also a tiny <a href="http://macstrac.blogspot.com/">Strac hack</a>  you can include in the Rails code. Basically the hack is to  set a reconnect flag when establishing a connection. The code is shown in the aforementioned thread.

<strong>(b) Risk mitigation - Automate monitoring and automatically redeploy when it fails</strong> I've always done silly things with cronjobs to automate redeployment, got the job done okay, but is definitely an admin smell. Nagios seemed too complicated. I just noticed <a href="http://www.tildeslash.com/monit/">this Monit tool</a> seems to be gaining traction in the Rails community and turned out to be pretty easy to set up. It wakes up every three minutes (by default) and runs a specified command if specified conditions are(n't) met. I hope <a href="http://www.capify.org/">Cap</a> or <a href="http://www.deprec.org/">Deprec</a> will introduce support for Monit in the future.