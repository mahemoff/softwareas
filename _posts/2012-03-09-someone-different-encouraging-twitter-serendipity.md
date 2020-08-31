---
id: 1569
title: 'Someone Different: Encouraging Twitter Serendipity'
date: 2012-03-09T02:38:07+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1569
permalink: /someone-different-encouraging-twitter-serendipity/
categories:
  - HumansAndTech
tags:
  - serendipity
  - Social
  - Twitter
---
I made a very raw cut of an idea that's been percolating for a while. The idea is to randomly follow a few people for a month or so, then rotate to a few different people, and so on. This would let you immerse yourself in a community for a little while, with the aim of busting out of [the filter bubble](http://www.thefilterbubble.com/), learning something new, and maybe making a new friend or two.

<b>Demo:</b> You can <a href='http://severe-sword-7058.herokuapp.com'>try a proof-of-concept here</a> (don't be put off by the permissions Twitter asks for; it won't tweet on your behalf, the permission is unfortunately necessary to manipulate lists). It's raw, but will create a real list for you and set its membership. It works now by simply switching to one of several manually-curated lists, which I just rotate when you visit the app (/pages/welcome). If there's interest, the plan is (a) to make the rotation happen automatically (b) generate the lists from something like Klout or PeerIndex, to ensure you're following people in the same community.

Right now, the "someone different" people live only in your "someone-different" list, but I'm inclined to follow them in the main stream. As long as they stay in the "someone-different" list, it's still easy to unfollow them from the main stream. And if you find you want to keep following someone, you just remove them from the "someone-different" list. (It's all very ghetto here; I'm basically using the twitter list in lieu of maintaining a database.)

I recently noticed @jobsworth was also looking for something like this. His ideas are certainly not achieved in this v0.0.1, but hopefully it will get people thinking about what's possible. Please let me know where you'd like to see this go.

<blockquote class="twitter-tweet" data-in-reply-to="173918851019448322"><p>@<a href="https://twitter.com/mahemoff">mahemoff</a> @<a href="https://twitter.com/kevinmarks">kevinmarks</a>I want collaborative filtering across lists *with a serendipitous twist of lime* leading me to weird and wonderful</p>&mdash; JP Rangaswami (@jobsworth) <a href="https://twitter.com/jobsworth/status/173920027035176960" data-datetime="2012-02-26T23:59:00+00:00">February 26, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

The app's built in Rails using the very nice <a href='https://github.com/mislav/twitter-login'>twitter-login</a> gem and hosted on heroku.