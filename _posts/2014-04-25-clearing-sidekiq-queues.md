---
id: 3
title: Clearing Sidekiq Queues
date: 2014-04-25T11:44:40+00:00
author: admin
layout: post
guid: http://qsoftwareas.com/?p=3
permalink: /clearing-sidekiq-queues/
categories:
  - Uncategorized
---
This is useful in development. Do this:

[ruby]

class SidekiqUtil

def self.queues
::Sidekiq::Stats.new.queues.keys.map { |name| ::Sidekiq::Queue.new(name) }
end

def self.clear_all
self.queues.each { |q| q.clear }
end

end

[/ruby]

Based on the [Sidekiq API](https://github.com/mperham/sidekiq/wiki/API)