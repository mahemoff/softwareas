---
id: 1316
title: Make Your Own Google Plus Feed
date: 2011-09-01T12:01:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1316
permalink: /make-your-own-google-plus-feed/
dsq_thread_id:
  - "401814072"
categories:
  - SoftwareDev
tags:
  - App Engine
  - GooglePlus
  - PlusFeed
---
![Plus Feed](http://farm7.static.flickr.com/6070/6102451639_01fc283b04.jpg)

### Background

I [recently mentioned](https://plus.google.com/106413090159067280619/posts/3TWDmpWtf8g?hl=en) why I like feeds as a developer:
<blockquote>I know RSS has been dead since 1982, but I'm still finding it very useful for powering status updates on my homepage (http://mahemoff.com). Whether Twitter, WordPress, Posterous, Lanyrd, Plancast, I know I can always scrape the most recent item with a one-liner.</blockquote>

It's not clear if and when Google will release RSS feeds for Plus, though the comments there certainly indicate they've given it a lot of thought. There's really too many variables to make speculation anything more than a fun discussion in the pub.

Fortunately, Russell Beattie has stepped up to make a third-party feed service, [PlusFeed](http://plusfeed.appspot.com). but it seems to have been hammered in 2 waves: first, by [an army of hungry feed bots](https://plus.google.com/104961845171318028721/posts/ajm6p3AZ9ER); and second, by [an increase in App Engine pricing](https://plus.google.com/104961845171318028721/posts/DamjzZBVxd7). Even at this early stage, it's costing $35/day, though there are probably optimisations possible as referenced in the comments.  (<strong>UPDATE: Russell's service is now offline due to the price whack, but the open-source project lives on. Follow the instructions here to roll your own for free.</strong>) 

In any event, since  [I'm using PlusFeed](http://softwareas.com/integrated-google-plus-on-the-homepage) for my homepage, I want to be sure it's running, so I wondered about writing my own feed service. But in a second stroke of awesome, I don't have to, as Plus Feed is actually [open source](https://github.com/russellbeattie/plusfeed). 

### Install A Feed Server on Google App Engine

It's very easy to fork and deploy PlusFeed, even if you've not used App Engine before ...

0. [Sign up for an App Engine account](https://appengine.google.com/) if you don't already have one, and [install the Python SDK](http://code.google.com/appengine/downloads.html#Google_App_Engine_SDK_for_Python). I recommend running the GUI for ease of use.
1. From your [App Engine dashboard](https://appengine.google.com/), hit "Create Application" and give your feed a unique name. Let's say "whataplusfeed".
2. Download Russell's project: <tt>git clone https://github.com/russellbeattie/plusfeed.git</tt>. (You may wish to fork it on GitHub so you can maintain your updates.)
3. You only need to make two changes - [here you can see what I did](https://github.com/mahemoff/plusfeed/commit/0f6e6440073064378248995fe3c31e0888a4ec20). Specifically, change the project name in app.yaml to "whataplusfeed". Then in plusfeed.py, replace the "idurls" regular expression with your own plus ID (the big number you see in your profile URL, e.g. https://plus.google.com/<b>106413090159067280619</b>/posts).
4. Import your project into the GUI, test it locally, and deploy it! Now your personal Plus feed is running at http://whataplusfeed.appspot.com/&lt;your-plus-id&gt;

You could easily whitelist a handful of IDs too, e.g. for all the staff in a company or a group of friends. Or you could just use the original project as is; it would make a nice public service, but unless a lot of others step up too, you're going to be liable for big bucks once the feed bots find your server. In any event, you can choose which feeds are offered by providing an appropriate regular expression in plusfeed.py (step 3).