---
id: 1464
title: Login Best Practices for Mobile Web Apps
date: 2011-11-14T22:52:01+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1464
permalink: /login-best-practices-for-mobile-web-apps/
dsq_thread_id:
  - "471904175"
categories:
  - HumansAndTech
tags:
  - Javascript
  - Mobile Web
  - Security
---
Walking home, I thought I'd venture to make a meal order via my phone...and without making a phone call. It shouldn't be an ordeal to do so in 2011, but frankly a sense of learned helplessness means I haven't even tried before. I know, #FirstWorldProblems, but let's learn something from it.

Anyway, I pull up my favourite meal delivery service, <a href="http://hungryhouse.co.uk">Hungry House</a> (highly recommended! At least in London.) I simultaneously launch a Market search for a Hungry House app - right or wrong, we know mobile app experience is almost always smoother. Well, no app, but the web page loads...and a bunch of antipatterns emerge.

Instead of documenting login antipatterns, I'll make this post more useful by turning them around and proposing best practices for mobile web login. Beware it's all speculative and subjective.

### Zen Login Form

Make a simple, mobile-optimised, login form. Make sure it's easy to click on each field to focus them (there's only two of them!). Make sure any links ("forgot password", "sign up") are far enough away they won't accidentally be licked.

This is true of all mobile web forms, not just login one. But if your app only works behind a login form, this would be the first one to optimise.

### "Keep Me Logged In" should default to On

It's a mobile phone, not an internet cafe, so yeah. Admittedly, this is trickier in the case of a tablet, but still it's only a default, I'm not saying "hide the option altogether". Also, <a href="http://www.html5rocks.com/en/tutorials/detection/">form factor detection ftw</a>.

### Don't Expire the Login Cookie

Okay, this will be controversial. But if mobile web apps are to be a viable alternative to mobile-native apps, they should provide the same login experience. Right now, a majorly overlooked distinction is login expiry. I find myself having to login to Twitter all the time, when trying to tweet from some other web app. But with the Twitter mobile app, I'm always logged in. Basically, mobile-native apps never expire the session. Most of them probably don't even bother with a session/token, they probably just store the user's credentials in plain text on the device (just some speculation on my part, based on the "see no evil" principle, given that this data is fairly invisible, being stuck in the app's data storage.) At least a cookie, if found by someone else, doesn't compromise the entire account, and can easily be expired.

### Keep it Light

Needless to say, don't load so much that the browser crashes. Repeated browser launches makes users hungry.

<a href='http://www.flickr.com/photos/avlxyz/4096745969/sizes/m/in/photostream/'><img src='http://farm3.static.flickr.com/2683/4096745969_29c3d3de20.jpg' /></a>