---
id: 2232
title: 'Progressive Web Apps have leapfrogged the native install model &#8230; but challenges remain'
date: 2016-04-05T10:12:56+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2232
permalink: /progressive-web-apps-have-leapfrogged-the-native-install-model-but-challenges-remain/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:11:"1c72251305b";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:40:"https://medium.com/@mahemoff/1c72251305b";}'
categories:
  - SoftwareDev
---
I visited Google's [Progressive Web Apps](https://events.withgoogle.com/progressive-web-apps-with-google/) shindig the other day and I'm pleased to see the progress browsers have made towards appiness in the past 2 years. Much of what [I wished for in frankly the web's darkest days](http://softwareas.com/state-of-the-browser-2-web-vs-native/) is now available in 3 major browsers and counting.

The install model has truly gone from being a non-starter to something that more closely maps the needs of users than any native platform has achieved. Here I will reflect on the current state of the web as a platform for apps, identify some remaining concerns, and propose where the biggest wins will come from.

## The web can do apps

While the HTML5 era (2008-2012, say) introduced many conventional app components, they emerged in parallel with the mobile revolution. I don't say "so-called revolution". It was an actual revolution in every way, changing forever how apps are designed, developed, and distributed. HTML5 was already ushering in a flood of new tech, it was never going to be possible to make it all mobile-savvy at the same time, and this led to a world where people went crazy for apps.

The progressive web movement plugs the gap in several ways: 

* Push notifications. These are lifeblood for many apps. Critical to the functionality of messaging apps like Skype and Slack, and - in a world of fickle users and high churn rates - vital to retention for all apps.
* Background processing. Doing stuff when the user doesn't have your app open is also vital for a modern app's functionality, performance and offline capability. This is about the app acting as your digital assistant, not just something you interact with for the time it's on the screen in front of you.
* Low-level APIs. As part of the [extensible web manifesto](https://www.w3.org/community/nextweb/2013/06/11/the-extensible-web-manifesto/), developers now get access to the low-level innards of the web stack. This not only helps the standards to evolve, but lets developers deliver useful functionality unanticipated by committee-driven standards processes.

Furthermore, it comes at a time when browser performance is strong and web debugging tools are built into all the major browsers and have become stupendously useful. All of which means, it's now possible to replicate the functionality and interface of many popular native apps.

But how will users install web apps?

Until progressive web movement came along, websites never had a chance on mobiles. Browser bookmarking features were about the same as in 1995 - just a flat list. Users didn't know how to install to homescreen and even with libraries prompting it, it gave no confidence the site would work offline. [Offline tech itself](http://alistapart.com/article/application-cache-is-a-douchebag), and the website couldn't do anything in the background as mentioned above above.

Now - with progressive web apps - two things have changed. Firstly - at least on Android - web apps have been elevated in their presence. The task switcher presents each recent website alongside each recent native app; they are all equivalent. The traditional 38-step "add to homescreen" process has been replaced by a simple menu item in Chrome. And most importantly, the browser will proactively prompt an install.

## The progressive web's install model rocks

A common argument for native apps has been the importance of app stores (insert $legally_acceptable_synonym for app store on your platform of choice). The web's counter-argument has heretofore been either "Ah but the web has search engines" or "Ah but there are x billion apps on the app store and only the top 10 get any installs". Neither of these arguments hold much water for me.

SEO is a real thing and search rankings are [as much or as little a meritocracy](https://twitter.com/mahemoff/status/636304152465920000/photo/1) as app rankings are. For every startup blowing $5K a day on Facebook app install ads, there's another startup paying for fake forum posts in the hope of Google juice. The "long tail" argument also applies just as much to the web.

So how does "progressive web" improve things? By letting users progress from a fly-by visit to a fully installed app, on their own terms.

The conversion funnel from "non-user" to "user" for a traditional app looks like this:

1. User discovers app.
2. User installs app. Waits a minute or two for download. App is installed.

Getting users from (1) to (2) is extremely hard for developers. Most users don't want to clutter up their phone with hundreds of apps, don't like to go through the hassle of downloading the app, and don't want to feel the remorse of installing a lemon (even a free lemon). Pulling off a large install base relies on a difficult-to-achieve store ranking, a viral loop that is fleetingly rare in practice, or several dollars of ad spend per paid install.

The progressive web install looks like this:

1. User discovers website.
2. User kicks tyres. Grants one or two permissions.
3. Re-visit or re-stumble on website a few times.
4. Say yes when browser prompts homescreen install (or explicitly install it).

This is a much more logical transition. Instead of making the install decision based on the store listing, the user makes the decision based on actually interacting with the app. At no point are they obligated to install it, but as they gain confidence in it, they can decide to do so. From the developer's point of view, it's easier to win long-term users if you have a product that's compelling (and if not, why do you care about installs? You will lose users anyway if you don't have good retention).

Admittedly, going from (3) to (4) is still hard. If the user hasn't yet installed the app, how confident can you be that they will re-visit your site often enough to be prompted? Part of the answer comes from background notifications, which means the user can still be engaged even without that install. As well, if the user's social contacts keep recommending the same app, it will likely lead to an install prompt. Compare that to a native share, which would often lead to nothing unless the content was amazingly compelling.

Indeed, it's likely developers will care less about installs in general, as long as they still have users who are engaged via notifications and spontaneous interactions they wouldn't see at the moment. Spontaneous usage is particularly compelling when you consider [the physical web](https://google.github.io/physical-web/). There's no way I'm going to install an app for the restaurant I'm in or the airport I'm flying to ... but I'll gladly open a rich web app from a prompt that shows up on my phone.

## Remaining concerns

So that's it huh? The web came back in the third act and triumphed. No. Not even. There are still many challenges ahead.

### Challenge: Apple ("There's a 586 billion dollar elephant in the room and it's not happy Jan")

Here are some facts about Apple, which - when combined - lead to skepticism about any efforts to progress the web:

* Apple and iOS are hugely influential. It's the platform companies care about most when it comes to development efforts.
* Browser innovation on iOS is controlled by Apple. Google, Firefox, and Opera may produce their own iOS browsers, but they will still run on Apple's engine and any progressive web tech on iOS therefore relies entirely on Apple's whims.
* Apple's incentives for browser innovation are "mixed" at best. While it wants a great user experience - including web interaction - it also has a lot to fear from a platform beyond its control that lets developers "write once, run many".
* Apple is sticky. Most mainstream users don't care about detailed OS features like homescreen widgets and notification interfaces. Even the tiny iPhone 4 screens were not enough for most users to look elsewhere. That was at least a very clear and visible advantage for the competition. So how much will users care about a better web experience if they can still get the same apps natively? It's a moderate OS benefit and may help Android (or other platform users) with retention, potentially clawing back market share in the long term, but it's unlikely to sway many users away from Apple. It's too difficult a concept to even explain, let alone for anyone to really care about it if they aren't already using it.

Don't hold your breath for an iOS which supports native-level video calling, gaming, and podcasting. Some features will make their way over time, but by then, there will be even more features on both native and - on other platforms - web. The only question worth asking is, how much does it matter?

For me, the answer is "not as much as you might think". People are still making web apps anyway. The whole thing about progressive web apps is they are progressive, not binary. So your web app can still work quite nicely on iOS, but do even more on other platforms. This won't apply to all genres, e.g. it's quite useless to make a voice calling app without push notifications.

Furthermore, there is a whole class of developers with iOS apps but lacking apps on Android, Windows, and other platforms. Enhancing their existing web presence is an increasingly bright alternative to hiring dedicated native developers, considering they usually have a web app and developers already (even more so if they are one of many companies now running Node/JavaScript on the server side). It may not give as perfect an experience as a native app, but it's infinitely better than doing nothing on those platforms and may well be as good as they would produce anyway outside of iOS.

### Challenge: Discoverability ("Websites on a plane")

It's still difficult to find good, installable, web apps. There are some hints when you're already using one - e.g. the prompts to install on home screen or receive push notifications, and the color scheme supported by the web manifest protocol. However, if I want to find an installable app to do X, where do I go? On native, I can just search in the store.

On web, I can search in ... Google? Nope. I'll usually get a pile of ugly and ad-ridden sites that happen to be old enough to have reached high rankings. Thankfully, Google does care more about performance and mobile-friendliness now, but it still doesn't come close to the app browsing experience of a native app store.

This is exactly what Chrome Web Store should be doing in 2016. I hope Google is working to finally bring the web store to native. (Or, amid much controversy, integrate web apps into Google Play.) And other browsers are similarly working on this problem.

Until then, there are [curated](http://mobilewebappsftw.tumblr.com/) [showcases](https://developers.google.com/web/showcase/?hl=en).

### Challenge: Native keeps moving forward ("2010 called.")

Native remains a fast-moving target. The web may have caught up on many features of a modern smartphone, but native has moved on to power virtual reality, cars, home appliances. Additionally, there are still many basic functions that aren't yet possible on the web, though they are being debated and worked on. e.g. I still can't make a full-fledged offline podcast app because of SSL and cross-domain restrictions. Bluetooth, USB, background audio ... these APIs are all being worked on, but aren't there yet.

### Challenge: Payments ("Shut up and take anyone's money")

Frictionless payments obviously drive a huge amount of activity in the app world and this is a realm where the web really hasn't changed since the introduction of smartphones. In-web payments is a complicated 4-way problem - there are users, browsers, operating systems, and payment providers. Add security, UX, and privacy to the mix, and now you see why there are casual games earning millions each day on native platform but nothing on the web.

If this can be cracked in the context of progressive web apps, game-changer.

### Challenge: Native app streaming is also progressive

The progressive engagement model is no longer exclusive to the web. Never afraid to boil the ocean, Google has now [begun previewing native apps](http://marketingland.com/google-app-streaming-web-of-apps-152449) by streaming them from the cloud. Yes, it relegates your device to a "dumb" display unit and runs the app on Google's servers, at least until you decide to install it. It's a very different type of progressive engagement, but it may steal some of the web's progressive thunder nonetheless, especially if Apple was to follow suit.

## Conclusion

Progressive web technologies are making it possible to go beyond just rich websites to "real deal" digital assistants like people have become accustomed to with native apps. The install model mirrors the way an app or service builds trust over time, and for this reason, it goes beyond the binary "installed or not" situation for regular native apps. While many challenges remain, the good news is ... it's progressive. Developers can already see the benefits by sprinkling in these technologies to their existing websites and proceed to build on them as browsers and operating systems increase support.