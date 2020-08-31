---
id: 1900
title: Shorthand Parameters
date: 2013-03-14T17:47:02+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1900
permalink: /shorthand-parameters/
categories:
  - SoftwareDev
tags:
  - Code
  - idioms
  - Ruby
---
Here is a weird abuse of default variable values to support shorthand variable names. It's valid Ruby.

[ruby]
def area(r=radius) {
  Math::pi * r * r
}
[/ruby]

Simple example, but you get the point. It lets you tell the external world what a parameter is all about, but keeps the implementation shorthand. Obviously it's just a simple example here; parameter names can be much more verbose than just this example and functions can be longer, so you don't want to keep repeating a long name. For example:

[ruby]
def damage_level(force_exterted_by_car=force) {
  force = 0 if force < 0
  acceleration = mass/force
  ...
}
[/ruby]

Now you might say "just declare it in the first line", but I prefer small code and there could be several such lines.

You might say "mention it in a comment", but I prefer self-documenting code. Comments go out of date and clutter up code. (Strictly speaking, the long name here *is* a comment, but it's more likely to be maintained.)

[Update: I don't often mention Pi, but when I do, it's on March 14: Pi Day. Thanks to the reader who pointed it out!]