---
id: 1882
title: Keeping SSH Alive on OSX 10.7.5
date: 2013-01-07T04:41:44+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1882
permalink: /keeping-ssh-alive-on-osx-10-7-5/
categories:
  - SoftwareDev
---
Quick SSH tip. I recently upgraded to OSX 10.7.5 and promptly found SSH sessions dying early and often. After trying various things people suggested, I found some flags which fixed it and am using this alias for now:

function shell { ssh -o TCPKeepAlive=no -o ServerAliveInterval=15 $1; }

You can [stick that in a config file](http://saschpe.wordpress.com/2009/11/25/ssh-session-timeouts/), if you wish to make it default.