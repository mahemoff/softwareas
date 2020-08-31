---
id: 2186
title: 'When your app composes tweets: Dealing with metadata'
date: 2015-09-21T01:33:52+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2186
permalink: /when-your-app-composes-tweets-dealing-with-metadata/
categories:
  - Uncategorized
tags:
  - Twitter
---
For those who don't know, Twitter converts every URL to its own "t.co" shortener URL. So no matter how short or long your original URL is, the t.co URL will end up as a fixed character length, and that character length does count towards the 140 limit.

Any sane Twitter client will hide this complexity from end-users. The word count algorithm will be smart enough to take this into account show the remaining characters.

But as a coder, you need to incorporate that logic yourself.

You should also know that Twitter's API won't automatically truncate a tweet, so if your app tries to send a long one, Twitter will return an error. So your tweet-posting app will need to truncate the tweet to 140 characters.

So I was coding up an auto-tweet setting, which requires you to estimate the length of a tweet. The code looks like:

[ruby]
TWEET_LENGTH = 140
TWITTER_URL_LENGTH = 19 // !!Danger - read on!!

def compose_message(episode)
   hashtag = '#nowplaying'
   url_and_hashtag_suffix = " #{episode.url} #nowplaying"
   max_title_length = TWEET_LENGTH - (1 + TWITTER_URL_LENGTH + 1 + hashtag.length)
   "#{truncate episode.title, max_title_length}#{url_and_hashtag_suffix}"
end
[/ruby]

And then, with a long title, it failed. Can you guess why?

The answer is because I apparently went to sleep for three years, and when I woke up, the world had composed [hundreds of billions of tweets](http://www.internetlivestats.com/twitter-statistics/). Many of them include URLs, which means the t.co length has crept up to 22 characters - 23 for SSL URLs - rising at about 1 character a year. Yes, if your tweet has a link in it, you now have to be 2.5% more concise in describing the link (that's 3/(140 - 19)).

Thankfully, there's an API for this:

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="en" dir="ltr"><a href="https://twitter.com/mahemoff">@mahemoff</a> there&#39;s a REST endpoint for that, it changes every so often <a href="https://t.co/9MMNp4oSh7">https://t.co/9MMNp4oSh7</a></p>&mdash; Andrew Lunny (@alunny) <a href="https://twitter.com/alunny/status/645696458608345089">September 20, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

So your code could periodically crawl [the config API](https://dev.twitter.com/rest/reference/get/help/configuration) and aggressively-cache the result. Or alternatively, have your build script download it to your code base at compile-time, if it hasn't seen an update for a while.

I haven't checked in detail, but there are probably some open-source Twitter packages (gems, NPM modules etc) that include this config data and keep it up to date.

Note this also affects images and video - the above config URL also provides the length of a media item.