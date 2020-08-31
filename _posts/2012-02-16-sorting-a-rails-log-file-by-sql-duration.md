---
id: 1503
title: Sorting a Rails log file by SQL duration
date: 2012-02-16T17:38:40+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1503
permalink: /sorting-a-rails-log-file-by-sql-duration/
categories:
  - SoftwareDev
tags:
  - Rails
  - sed
  - sysadmin
  - Tuning
---
Rails' ActiveRecord logger writes log files like:

<code>Post Load (735.8ms)  SELECT `posts`.* FROM `posts` where post.title = 'foo'
</code>

You may want to know the longest SQL queries for performance optimsation purposes, and general troubleshooting. To list recent queries in order of duration, with longest queries shown last, use this:

<code>
head -10000 development.log | grep '([0-9.]+ms)' | sed 's/.*(([[:digit:].]+)ms.*/1ms &/g' | sort -n
</code>

(The sed expression was a little more work than I'd bargained for as sed regular expressions are always lazy; even with GNU/Posix extensions, non-lazy just doesn't exist.)