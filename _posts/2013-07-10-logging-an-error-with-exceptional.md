---
id: 1927
title: Logging an error with Exceptional
date: 2013-07-10T11:30:22+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1927
permalink: /logging-an-error-with-exceptional/
categories:
  - SoftwareDev
tags:
  - Rails
  - Ruby
---
Here's a quick utility for people using [Exceptional](http://exceptional.io) to track errors.

<script src="https://gist.github.com/mahemoff/5965516.js"></script>

It lets you force an exception to be logged and without having to rescue it. Example:

exceptional "read_file", "file not found"