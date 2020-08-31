---
id: 1954
title: 'Rails quirk: Adding to DateTime'
date: 2014-04-23T08:06:49+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1954
permalink: /rails-quirk-adding-to-datetime/
categories:
  - SoftwareDev
tags:
  - Ruby
---
Just came across a weird one with DateTime. Adding an int value will increment by a day, not a second as you may expect:

[ruby]
$ x=1
1
$ x.class
Fixnum
$ DateTime.new(2000, 1, 1, 0, 0, 0)+x
Sun, 02 Jan 2000 00:00:00 +0000
[/ruby]

But adding by a second *is* possible using explicitly 1.second. The strange thing is both inherit from FixNum and essentially act as the same number. So if you want it to mean seconds, one way to achieve it is use "x.seconds".

[ruby]
$ x=1.second
1 second
$ x.class
Fixnum
$ DateTime.new(2000, 1, 1, 0, 0, 0)+x
Sat, 01 Jan 2000 00:00:01 +0000
[/ruby]