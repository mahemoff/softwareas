---
id: 1652
title: Web Vs Native at State of the Browser 2
date: 2012-04-29T13:26:10+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1652
permalink: /state-of-the-browser-2-web-vs-native/
categories:
  - SoftwareDev
tags:
  - Conference
  - html5
  - Web
---
<a href="http://imgur.com/O8rIu"><img src="http://i.imgur.com/O8rIu.jpg" alt="" title="Hosted by imgur.com" /></a>

(via [Steve Workman](http://www.steveworkman.com/html5-2/standards/2012/state-of-the-browser-2012/comment-page-1/#comment-1185))

I was at State of the Browser 2 yesterday, an event comprising reps from the browsers. I'm happy to be part of this event as I think it's valuable for the web as a whole for devrels to get together with developers in this way. The browsers do spend a lot of time talking to each other about specs etc in meetings and mailing lists, but at State of the Browser, they're facing the developers. So straight up, thanks to the organisers for doing a great job running this great event again.

<a href="http://twitpic.com/9eojfe" title="Share photos on twitter with Twitpic"><img src="http://i.imgur.com/8C9vC.jpg" width="400"></a>

Thankyou for the sketchnotes UBelly :)

[Slides for my keynote talk on Web vs Native are here](http://prez.mahemoff.com/state-native/). I'll highlight the four challenges of the web which 

In order of increasing threat, I mentioned:

* *UI* Low threat. A lot of the capabilities are already in place and we can already do decent UIs if not "gorgeous"/"sexy" like Path or Paper.

* *Offline* Medium threat. DHH wrote his famous [You're Not on a Plane argument](http://37signals.com/svn/posts/347-youre-not-on-a-fucking-plane-and-if-you-are-it-doesnt-matter) in the desktop era. Mobile is way important these days, connectivity remains sketchy, and 3G is expensive for many. The pure offline scenario may matter less, at least for many people in developed nations, but latency matters a lot to everyone. HTML5 does have offline technologies, but browser support is extremely fragmented and there are many debates about what to use where.

* *Device Integration* Medium threat. Web needs permissioned access to camera, contacts, etc. But my bigger concern is peripheral aspects like single sign-on, notifications, Android intents. These things, for the most part, are not possible in web apps. There are signs that's changing as the speakers yesterday highlighted, e.g. Chrome's adding Web Intents, IE's adding native notifications like the OSX native notifications I mentioned. But it's really early days, and I don't see anyone talking about single sign-on for web apps, which is hugely concerning considering how personal in nature smartphones and native apps are.

* *Background Processing* High threat. This doesn't get much play, but is something I've been thinking about since [writing this](http://softwareas.com/non-visual-web) and listening to the related Jason Grigsby podcast. With modern smartphone apps, we see the long-anticipated trend of software that acts as intelligent agents. An app is not just something you open, interact with, and close. Through its smartphone vehicle, the app serves as an extra brain, extra set of eyes and ears, extra communication agent. With you at all times, proactively scanning the environment for anything useful. Sucking down content and syncing with servers. Notifying you when anything particular important happens. Web apps are shut out of this game. They are useful as long as the user is looking at them. Out of sight, out of mind. Or more generously, as long as they are still open in a tab, but they may have restricted functionality in mobile background tabs to preserve battery life. Chrome has done some work here with background apps, but it's really early days and I don't see anyone thinking about this problem in mobile space.

I also mentioned monetization and competing standards as additional threats, only reason I didn't cover them in detail is time. I did mention a little of it in the recent [bonus HNPod episode on HTML5 vs Native](http://hnpod.com/episodes/html5-vs-native-apps) and [we had a Twitter conversation about it yesterday](http://storify.com/mahemoff/in-web-payments).

[Remy blogged all the morning talks](http://remysharp.com/2012/04/28/notes-from-state-of-the-browser/) and raised some questions about each.

*Is the point: browsers don’t matter – the web does…?*

The underlying assumption is that the web matters more than any individual browser.

*Should the browser just be the webview?*

No. Browsers add a lot of value beyond the web view. One of many examples is customisation via preferences and extensions.

*“You’re not on a fucking plane” – but then do all devs know how to build apps like gmail where it’s insanely quick because they know how to work the mobile device?*

Agree. It's hard right now. And even harder if you wish to use the same core app for both online and offline (as well as desktop and mobile).

*AppCache is not a replicatement (sic.) for localStorage – far from it.*

Definitely not.

*Is there a larger problem that the browser (and a pro) exposes data if the user wants to get to it. It makes SSO harder because of security, etc?*

Yes, but just like camera access, geolocation, etc, you can handle it with permissions. If HTML5 doesn't stay competitive with native on SSO, background apps, etc, it's not going to be a modern platform for apps. There's enough UI widgets already, it's these peripheral aspects &mdash; those where security is an issue &mdash; where native is surging ahead. You can either do basic websites without app-iness or you can do apps which use the full range of possibilities available in a modern device and operating system.

*Web vs. Native seems like two issues: browser and the web. Browsers being the limitation*

Both as we'd want web standards too for whatever the browsers offer developers. But definitely down to the browsers and possibly the OSs when you consider SSO for example.

![](https://lh3.googleusercontent.com/-TZWDF_2XkMk/T50x6LaQIlI/AAAAAAAADrk/5a_IF2oW7KU/s773/terbi.jpeg)

The panel I moderated. Devrels from four browsers and the forbidden fruit. ([via james_smith88](https://twitter.com/james_smith88/status/196301531396575233/photo/1))