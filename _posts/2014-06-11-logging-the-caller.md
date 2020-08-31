---
id: 1981
title: Logging the caller
date: 2014-06-11T23:29:29+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1981
permalink: /logging-the-caller/
categories:
  - Uncategorized
tags:
  - Logging
  - Ruby
---
It's so useful to automagically log caller line number and so on. Most languages make it possible via hack involving throwing an exception to yield a stack trace. Some languages explicitly provide this info. In Ruby, it's possible with the `caller` array.

Here's how I used it just now:

[ruby]
def logg
  caller_info = caller[0].gsub! /^.+\/(.*)\.rb:(.*):in `(.*)'/, '\\2:\\3:\\2'
  Rails.logger.debug "[#{caller_info}] - #{id}. Thread#{Thread.current.object_id.to_s(36)}"
end
[/ruby]

This will output caller_info in the format: `[series_feed:fetch:123]`. Which is the `file:method:line_number`. It's derived, via the initial regex, from the slightly less log-friendly caller string, `path/to/series_feed.rb:123:in `fetch'.