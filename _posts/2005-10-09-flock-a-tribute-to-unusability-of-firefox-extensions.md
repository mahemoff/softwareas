---
id: 212
title: 'Flock: A Tribute to Unusability of Firefox Extensions?'
date: 2005-10-09T23:24:05+00:00
author: admin
layout: post
guid: http://www.softwareas.com/flock-a-tribute-to-unusability-of-firefox-extensions
permalink: /flock-a-tribute-to-unusability-of-firefox-extensions/
dsq_thread_id:
  - "375572615"
  - "375572615"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Browsers
  - Extension
  - Firefox
  - Flock
  - Greasemonkey
  - Plugin
  - Software
  - Software Architecture
  - Web
  - Web 2.0
---
You've probably noticed the buzz around [Flock](http://flock.com), a browser built on Firefox. Information's limited, but it seems to pick up on the "social" buzzword - tagging, annotations, RSS etc. **Thing is, all of these things are possible in Firefox too via extensions. But extensions haven't really taken off, and the reason is, quite frankly, poor usability.** Firefox is a great browser with a plugin architecture that's pretty good too. The problem is at the last mile: helping users install and manage their extensions.

**Sure, developers will install programming extensions and uber-geeks will set up mouse gestures, but it won't get beyond that in its current state.**

So here's how a plugin architecture *should* work:

* **Installing plugins should be dead simple.** Pull up a list of plugins and click to install ... that's it! Come on, you own the whole browser and the server too! Make them work together. The current task is something like "visit extensionroom, search for extension, jump into extension page, click Install, Notice security dialog box about this subdomain if you're lucky, Allow the subdomain, Click Install again if you're savvy enough to realise what just happened, Watch it download, Click Install, Restart the browser if you're still interested". If the version's incompatible, you'll only find out at the end of all that (except the restart). True, the version number's shown when you install it, but that's really making the user do something the computer should do immediately. Also, most users don't remember what version they're running, and I've even seen extensions with the version labeled as "Deer Park".
* **The standard distribution should have a set of extensions pre-installed.** Just because you're using a plugin architecture doesn't mean you have to ship with a bare-bones distribution. I know there are potentially licensing issues, but shipping with plugins seems to work OK for Eclipse and similarly for the Linux distributions. Satisfy the slashdot crowd with a minimal distribution too, by all means, but mainstream users would rather not spend three hours working out how to install extensions, finding out which are popular/useful, discovering incompatibilities between different extensions, etc. There are plenty of extensions that enhance basic functionality - e.g. All-In-One Sidebar, Adblock, the improved search bars, the improved RSS aggregators - why not take advantage of them? In addition, there's great scope for specialised distributions, e.g. Developer, Socialite. I know anyone could probably make them and distribute them, my main point here is that Firefox itself should at least distribute a more powerful default distro.
* **Don't rely on third-party extensions for fundamental functionality.** Tabbed browsing works OK in the basic distribution, but the Tabbrowser extension gives it much more power - certainly it brings it up to Opera standard. Yet, it's been unsupported for over a year, confusing, and buggy at times. Something like this is too important to leave to a third-party. Develop it as an extension if it's architecturally convenient to do so, but make it mandatory, so that other extensions play nice with it.
* **Provide update notifications.** Indicate when updates are present and offer to do the update automatically.

Greasemonkey took off so quickly because it's so easy to develop, modify, and install GM scripts. Hopefully, the lessons of Greasemonkey and the imminent release of Flock will offer some lessons, and help make Firefox  an even greater browser.