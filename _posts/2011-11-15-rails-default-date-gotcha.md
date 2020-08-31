---
id: 1469
title: Rails Default Date Gotcha
date: 2011-11-15T05:41:29+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1469
permalink: /rails-default-date-gotcha/
dsq_thread_id:
  - "472216018"
categories:
  - SoftwareDev
tags:
  - Rails
---
This had me going for a while!

I wanted to default a field to the epoch, i.e. some decades ago, or older. That's because a batch process will work on the records with the oldest such field, so setting the field to epoch guarantees they'll get priority initially.

I had a migration like such:

[ruby]
  t.datetime :acted_on, :default => 0  ### BAD
[/ruby]

After some debugging, I notice [FactoryGirl](https://github.com/thoughtbot/factory_girl) is setting the field to null. The fix is:

[ruby]
  t.datetime :acted_on, :default => DateTime.new ### GOOD
[/ruby]

Note it's DateTime.new for epoch, not DateTime.now, which will be the present time. (And you probably wouldn't want that, because it would be the time you run the migration, not the time a given record is actually created. If you want creation time, use a before_create callback.)