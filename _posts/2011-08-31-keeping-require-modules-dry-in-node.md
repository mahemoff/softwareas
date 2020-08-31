---
id: 1314
title: 'Keeping &#8220;require&#8221; modules DRY in Node'
date: 2011-08-31T20:11:29+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1314
permalink: /keeping-require-modules-dry-in-node/
dsq_thread_id:
  - "401240841"
categories:
  - SoftwareDev
tags:
  - CoffeeScript
  - Convention Over Configuration
  - DRY
  - Javascript
  - Modules
  - NodeJS
---
Update: See the [follow-up](http://stackoverflow.com/questions/7262869/best-way-to-require-several-modules-in-nodejs) on StackOverflow. I agree with those who rallied against use of global, but no need to throw the baby out with the bathwater; as shown in that thread, we can instead use "eval" to keep it DRY.

You see a lot of NodeJS code like this:

[javascript]
connect = require 'connect'
express = require 'express'
redis = require 'redis'
sys = require 'sys'
coffee = require 'coffee-script'
fs = require 'fs'
[/javascript]

BTW this is CoffeeScript, not pure JavaScript, but the same logic applies.

The point is, Node's module system gives you a layer of abstraction you probably don't need. 9 times out of 10, people just assign a module to a variable by the same name. You would, wouldn't you?!! You don't have to think about alternatives, and you can easily cut and paste other people's code. And it's now just an industry convention.

So why not practice [convention over configuration](http://en.wikipedia.org/wiki/Convention_over_configuration), and keep things [DRY](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself) with the following idiom:

[javascript]
"underscore,connect,express,redis,sys,coffee-script,fs"
  .split(',').forEach (lib) -> global[lib] = require lib
[/javascript]

Thanks to the "global" object, which is like the "window" object in the browser, we can easily require new libraries without unnecessary clutter.

And - as with any decent convention-over-configuration setup - we can still override the convention if we desire:

[javascript]
_ = underscore
[/javascript]