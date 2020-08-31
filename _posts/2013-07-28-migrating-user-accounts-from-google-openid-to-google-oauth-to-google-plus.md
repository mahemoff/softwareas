---
id: 1929
title: Migrating user accounts from Google OpenID to Google OAuth to Google Plus
date: 2013-07-28T20:44:12+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1929
permalink: /migrating-user-accounts-from-google-openid-to-google-oauth-to-google-plus/
categories:
  - General
  - SoftwareDev
tags:
  - Google
  - OAuth
  - Open ID
  - Player FM
---
### Background

[Over here](https://plus.google.com/105984166910030353519/posts/ToWYJXctnGy), [Ade](http://www.oshineye.com/?) has asked me to permalink a comment I made about moving [Player FM](http://player.fm) accounts from Google Open ID to OAuth. The reason I did it was because Android sign-in is really based on OAuth, but what I didn't know was Google at the time was preparing to launch "Sign in with Google Plus", also based on OAuth. Bottom line: Google Open ID, afaict, is going the way of the dodo, so any services using it probably want to migrate their users to G+. (Googlers may please correct me if I'm wrong about Open ID's demise.)

There were many permutations to be considered for this kind of migration, each with trade-offs to developer complexity and user experience. What follows was the optimum balance for me after a repetition of thought experiments, in between wishing I had a pony (ie that I'd opted for OAuth in the first place, the only reason I didn't was availability of an Open ID Rails plugin). This is all web-based as we (thankfully) hadn't launched on Android yet.

### The problem

The first concern here is largely about user perceptions. To us developers, Google OAuth and Google Open ID are distinct login mechanisms, as similar to each other as they are to Facebook or Twitter. But to the user, they're the same thing - Googles all the way down. So you can't present the user with separate login buttons for Google OAuth and Google Open ID...you only get to present one Big G button.

The other concern is that sites who present "Existing users - log in here" versus "New users - sign up here" buttons ... are doing it wrong. A major benefit of third-party sign-in is you can just present a "Connect with X" button and the user doesn't have to care or remember if they previously connected with X or not. Don't make me think!

Put concern A together with concern B and Houston, we have a problem. You present that one big G button with Google OAuth and what happens if the user is unrecognised? Is this a new user or someone who had previously logged in using Open ID. (It's fine if the user *is* recognised, that means they're one of the post-OAuth-era people.)

### The solution

The solution depends if you're willing to ask for email permissions on the new oAuth flow.

If you *are* willing to ask for email, that will make it easy to link the two accounts, because Open ID already relies on email, so you have their email. You can just switch right now to oAuth and once the user authenticates, link the account with the account having the same o8 ID. (Note: this scenario is purely speculative and not based on my experience.)

Since I chose not to ask for email, I had to do the uncool thing and temporarily divided Login from Signup.

In the Login area, the app prompted users for their email or login, and immediately made an XHR call to detect whether that account is using o8 or oAuth, then showed the corresponding button (the button is just a Google button, looks the same either way but the link will be different for o8 vs oAuth). (In addition, the Twitter and classic login form were shown.)

For people who logged in with Open ID, I built an !IMPORTANT! big red notification when the user logged in via Open ID, telling them we've updated Google login procedure, and when they click to set it up, taking them through the oAuth flow with a special callback for the migration. At this point, the server recognises the two accounts are linked (they'd already logged in with Open ID, now they've just logged in with OAuth), so we can save the user's OAuth credentials. This user now has two third-party accounts - Google Open ID and Google OAuth. Just as they might also have a Facebook account and a Twitter account.

The Signup area of course only contained an OAuth button (as well as Twitter, which was exactly the same as Twitter in the login area, and classic signup form).

I published advance notice on the blog I would be shutting down the old Google IDs, kept the migration alive for two months, and then deleted all the Open ID accounts at that time. Anyone who didn't log in at the time lost their accounts, but of course a few people mailed me about it (mainly when we launched the Android app and they tried to log in again), so I helped them migrate manually.

I did this for a couple months before deprecating o8 and returning to the nicer single Google button setup. And just manually merged the accounts when a few users asked me why the Google button is not getting them back to their old account.?

### Epilogue

It was well worth the pain, as the vast majority of Android users now choose to log in with Google, even though we also support classic login and guest mode. The G+ API was a big bonus to come out of it. I've done some experiments on the social side and expect to do much more with G+ accounts in the future, to help people discover new shows to listen to.