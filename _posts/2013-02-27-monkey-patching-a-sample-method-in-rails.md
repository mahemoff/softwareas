---
id: 1892
title: Monkey-patching a sample() method in Rails
date: 2013-02-27T03:22:06+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1892
permalink: /monkey-patching-a-sample-method-in-rails/
categories:
  - SoftwareDev
tags:
  - ActiveRecord
  - Rails
  - random
---
It's useful while debugging to choose a random sample. Thus you can include something like this in application.rb or an initializer.

<script src="https://gist.github.com/mahemoff/5044718.js"></script>

Now you can say `Post.sample` to get a single post or `Post.sample(5)` to get 5 of them.

See also [here](http://thinkingeek.com/2011/07/04/easily-select-random-records-rails) and apparently [the randumb gem](https://github.com/spilliton/randumb) will extract random ActiveRecords too.