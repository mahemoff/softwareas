---
id: 2128
title: Android M Highlights
date: 2015-05-30T18:52:11+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2128
permalink: /android-m-highlights/
categories:
  - Uncategorized
---
<img src='http://i.imgur.com/VrUwLJk.png'>

Google IO has now wrapped up. The conference went smoothly and overall there has been a decisive swing back in focus towards developers. Android remains the centerpiece, in terms of the keynote, schedule, and displays, and Android M is now here and available to developers.

Here are some highlights of Android M following IO. I haven't yet tried it, though I'll be flashing the giveaway N9 before long.

### Mmmm ... that name

If two makes a pattern, Google has now established the single-letter name convention for developer preview editions. I suppose this goes along with IO's renewed focus on developers, in contrast to the actual OS release (which normally coincides with the new Nexus line, about 6 months later). Google gets to save the name reveal for the fanfare it really wants around that time. Any problems that happen along the way will be associated with M, not the eventual name. And finally, it also lets them defer a decision, which is usually a Good Thing, and especially when it involves other companies (Kit Kat).

Anyway ... if it's not <s>marshmallow</s>MarshMallow, I'll be disappointed.

### On-demand permissions! Finally

Android M joins iOS, Cyanogenmod, and the web in supporting on-demand permissions, a feature that had been [experimented with previously](http://techcrunch.com/2013/07/26/android-app-ops/) but didn't see the light of day until now. This is great news for both users and developers. Improved security and control for users, and meanwhile developers don't have to get caned for providing rich, optional, features.

One recent example was Player FM supporting audio ducking, ie the ability to keep playing when a transient sound plays. Because phone calls are also transient sounds, we had to declare a permission to detect when the phone was ringing, which happens to include the ability to see the user's phone number and those they call. All this for an optional setting. Not surprisingly, there were many queries about the new permission and I'm very pleased it can be optional with M.

### App Linking

A developer can now [tie its app and website together](https://developer.android.com/preview/api-overview.html) by, in crude terms, pointing each to the other. The net effect is users can click on a link without being presented with the tedious "Open with ..." menu. It will open straight in the app if it's installed. I believe these menus are one of the biggest UX problems for Android, as they appear far too often (basically, anytime an installed application has declared a regexp matching the link you just click). This doesn't solve the problem completely, but is a major step in that direction.

It will also be a controversial feature, as it means any site can now block third-party apps from "presenting" or "hijacking" (depending which side you're on) its links. By declaring its the one and only app to handle those URLs, other handlers are shut out. It's true, at least in this initial M build, that users can modify those settings, but few will go to those lengths.

### Custom Chrome Tabs

App linking is about jumping from one app to another. Custom tabs is about jumping from an app to the web. It's actually a Chrome update, so once it lands in Chrome, it should work on older Android too.

Consider what happens when a link needs to open a web page? One solution is for the app to host its own webview, thus keeping the user from leaving their app and retaining their controls and branding. This unfortunately leads to a cottage industry in "optimising your website for Twitter/Pinterest/Facebook webviews". The webview, being a sandboxed environment, is slow to load as caching isn't possible, and nor does it inherit cookies or the user's browser settings. So, not ideal.

Custom tabs aim to get the best of both worlds: custom controls and branding, but inside "actual Chrome". Even the transition between browser and app can be configured, and pre-caching is also possible, ie telling Chrome to start loading something while the user is inside the app.

### Direct Share

Direct share is a new standard for the popular pattern of sharing something with N friends. The technology is similar to the file picker introduced in Kitkat - where the file picker could let you choose a file from any of Dropbox, Google Drive, etc, the new share feature is effectively a "people picker" that lets you share with contacts or any participating social network. This is also about Google recognising Google Plus is not the only answer to social on Android.

### Doze State

Doze is the apt name for a new state that kicks in when the phone is still for a long time. Apps go into background but notifications and alarms still work. It makes sense as a trade-off and will be brilliant if it even gets close to the "up to two times longer" standby lifetime.

### Play Store: 

Technically Play!=Android, but hey it's the main distribution point, and there were some important updates. A-B testing of the description will be possible with the new experiments feature. Analytics on ad revenues and conversions will be available directly in Play. And there will be a new family-friendly Play store with some apps there being verified as family-friendly.

[<i>Image credit</i>](http://news.softpedia.com/news/Android-M-Is-Coming-Here-s-a-Few-Features-We-Want-to-See-480678.shtml)