---
id: 2160
title: Speeding up Rails tests with Spring
date: 2015-07-28T14:05:04+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2160
permalink: /speeding-up-rails-tests-with-spring/
categories:
  - Uncategorized
tags:
  - Rails
---

I found Rails tests were running slow, these things helped.

### Instrumenting application.rb

First, I added some logging to application.rb

[ruby]
def logg(m)
  puts "#{DateTime.now} #{m}"
end

logg 'require boot'
require File.expand_path('../boot', __FILE__)
logg 'done'</code>
[/ruby]

The main bottleneck was bundling (`Bundler.require(:default, Rails.env)`), which took around 12 seconds on OSX.

### Goodbye Bundle?

10+ seconds delay for running a test is unacceptable, leading me to contemplate [ditching Bundler](http://myronmars.to/n/dev-blog/2012/12/5-reasons-to-avoid-bundler-require). However, that's a lot of manual overhead, requiring us to manually import stuff, and we're using Ruby here because it's supposed to cut out tedium like that.

### Spring forward

The real answer is to avoid running application.rb every time using the (defaultly-installed) Spring. Spring should keep a master process around after the app has booted, so we don't need to run application.rb every time. I thought [Spring](https://github.com/rails/spring) was already running, but with this kind of delay, I had to check it.

Opened a new terminal, started tailing /tmp/spring.log, and then made spring start using it in the main Ruby test running terminal:

[bash]
spring stop
export SPRING_LOG=/tmp/spring.log
tail -f /tmp/spring.log
[/bash]

This is perfect for diagnosis: I have the aforementioned application.rb logs in the main terminal and the other window shows me what Spring is up to.

Ran a test:

[bash]
truby test/models/user_test -n /username/ # truby is my alias for RAILS_ENV=test bundle exec ruby ...
[/bash]

And yes, I saw application.rb running through all the motions, 10 second bundle, etc. And no spring action.

Ran it again.

Same thing. We're booting the whole app for every one of these tiny tests!

The thing is *Spring only works for a select few commands* - any rake command and just a few Rails commands (rails console, rails generate, rails runner). This caught me out as I was trying to run `rails server` and Spring again wasn't running. I guess the thinking is you shouldn't need to restart web server often in dev anyway - stuff is already auto-reloaded according to default config.

So the answer was to run tests through Spring. I'd previously stopped doing that due to difficulty running a single test method, but now it's easy.

[bash]
rake test test/models/user_test /username/
[/bash]

In the above case, the second argument is an optional test method or regular expression. Unlike the direct invocation, no "-n" is needed if a regex is provided.

And, problem solved. I see Spring is cloning the booted process and the test runs in a fraction of a second.