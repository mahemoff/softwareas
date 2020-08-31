---
id: 425
title: 'SSH Tip: Remember Last Path'
date: 2008-02-14T08:16:14+00:00
author: admin
layout: post
guid: http://softwareas.com/ssh-tip-remember-last-path
permalink: /ssh-tip-remember-last-path/
dsq_thread_id:
  - "375573534"
categories:
  - SoftwareDev
tags:
  - ssh
  - Unix
---
<tags>ssh, Unix</tags>

Lately, I've been living dangerously and doing a lot of coding on the live server, via ssh. This is all proof-of-concept stuff at <a href="http://ajaxify.com">Ajaxify</a>. The reason I'm coding live is that it's all widget development and it's just easier that way, since environments like iGoogle and Facebook need to reach my apps live, in order to test the app. None of the alternatives take my fancy: open up a port into my development PC (difficult due to dynamic DNS and less secure); upload code each change (slow even if it's fully scripted); use <a href="http://incubator.apache.org/shindig/">Shindig</a> on my local machine (unreliable as Shindig is new and in rapid growth mode).

So I've been ssh'ing and no matter how many times I've tried, I can't remove ssh timeout, so I sometimes get timed out. So anyway, I wanted an easy way to remember the most recent directory I was in, each time I log back in. This is it - in my .bash_profile:
<pre>
function cd { builtin cd $1 ; pwd > $HOME/.path_history; }
cd `cat $HOME/.path_history`
</pre>