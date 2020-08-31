---
id: 1686
title: Calling Twitter When Using Devise
date: 2012-06-15T13:26:31+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1686
permalink: /calling-twitter-when-using-devise/
categories:
  - SoftwareDev
---
A little tip, as this took some hunting around.

So you've added Twitter login via Devise. How do you then make signed Twitter calls on behalf of authenticated users?

UPDATE: Made a little module for this, at the end of this post.

Your Devise config (initializers/devise.rb) looks like this:

[ruby]
config.omniauth :twitter, 'this-is-my-consumer-id', 'this-is-my-consumer-secret'
[/ruby]

To make a Twitter call signed by the user, you'll need to access that config data. Here's how:

[ruby]
twitter_config = Devise.omniauth_configs[:twitter]
consumer_key = twitter_config.strategy.consumer_key
consumer_secret = twitter_config.strategy.consumer_secret
[/ruby]

Now using [twitter-oauth gem](https://github.com/moomerman/twitter_oauth), you can make a call like so:

[ruby]
t = User.find('joe').user_tokens.where(provider: twitter)
twitter = TwitterOAuth::Client.new consumer_key: consumer_key, consumer_secret: consumer_secret, token: t.token, secret: t.secret
twitter.search 'groo'
[/ruby]

You can find [the full list of Twitter OAuth API calls in the source](https://github.com/moomerman/twitter_oauth/tree/master/lib/twitter_oauth).

Here's a module that does this, which you can mix into User models:

<script src="https://gist.github.com/2937018.js?file=twitvise.rb"></script>
