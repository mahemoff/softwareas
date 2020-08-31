---
id: 1165
title: 'Live Blog: PPK on the Future of the Mobile Web'
date: 2011-05-11T14:09:11+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1165
permalink: /live-blog-ppk-on-the-future-of-the-mobile-web/
dsq_thread_id:
  - "375550527"
categories:
  - SoftwareDev
tags:
  - Apps
  - Conference
  - html5
  - Mobile Web
---
<em>This comes from <a href="http://ppk.eventbrite.com/">a talk on mobile web</a> given by PPK the last time I was in this part of the world, before a full house at the very large eBay/PayPal "town hall" in San Jose on April 6. I decided to hold off posting it as he mentioned he's not releasing the slides so he can deliver the same talk a few more times. With two imminent talks on mobile HTML5 today at Google IO, timing is right to hit the Publish button.</em>

<em>This is still a live blog (I'm far too lazy to edit such things even after the event), so usual typo etc caveats apply.</em>

<a href="http://gijsvanzon.posterous.com/peter-paul-koch-about-the-future-of-mobile-we"><img style="width:500px;" src="http://picupper.com/2011/05/11/ppk.jpg"></a>

<span style="font-size: small;">(>Picture from a <a href="http://gijsvanzon.posterous.com/peter-paul-koch-about-the-future-of-mobile-we">different event</a> on the same topic...but how could I not include this one?)</span>

Amid a frenzy of mobile HTML5 hacking at the HQ, I spot a tweet from the veritable @dalmaer:

<!-- http://twitter.com/#!/dalmaer/status/55764706551529472 --> <style type='text/css'>.bbpBox55764706551529472 {background:url(http://a1.twimg.com/profile_background_images/171762394/setdirection_bg_twitter.jpg) #40ACDA;padding:20px;} p.bbpTweet{background:#fff;padding:10px 12px 10px 12px;margin:0;min-height:48px;color:#000;font-size:18px !important;line-height:22px;-moz-border-radius:5px;-webkit-border-radius:5px} p.bbpTweet span.metadata{display:block;width:100%;clear:both;margin-top:8px;padding-top:12px;height:40px;border-top:1px solid #fff;border-top:1px solid #e6e6e6} p.bbpTweet span.metadata span.author{line-height:19px} p.bbpTweet span.metadata span.author img{float:left;margin:0 7px 0 0px;width:38px;height:38px} p.bbpTweet a:hover{text-decoration:underline}p.bbpTweet span.timestamp{font-size:12px;display:block}</style> <div class='bbpBox55764706551529472'><p class='bbpTweet'>@<a class="tweet-url username" href="http://twitter.com/AndreCharland" rel="nofollow">AndreCharland</a> come to the @<a class="tweet-url username" href="http://twitter.com/PPK" rel="nofollow">PPK</a> meetup tonight! A bunch of folks are going :)<span class='timestamp'><a title='Wed Apr 06 22:51:56 +0000 2011' href='http://twitter.com/#!/dalmaer/status/55764706551529472'>less than a minute ago</a> via <a href="http://itunes.apple.com/us/app/twitter/id409789998?mt=12" rel="nofollow">Twitter for Mac</a> <a href='http://twitter.com/intent/favorite?tweet_id=55764706551529472'><img src='http://si0.twimg.com/images/dev/cms/intents/icons/favorite.png' /> Favorite</a> <a href='http://twitter.com/intent/retweet?tweet_id=55764706551529472'><img src='http://si0.twimg.com/images/dev/cms/intents/icons/retweet.png' /> Retweet</a> <a href='http://twitter.com/intent/tweet?in_reply_to=55764706551529472'><img src='http://si0.twimg.com/images/dev/cms/intents/icons/reply.png' /> Reply</a></span><span class='metadata'><span class='author'><a href='http://twitter.com/dalmaer'><img src='http://a0.twimg.com/profile_images/292949152/dionprofile_normal.png' /></a><strong><a href='http://twitter.com/dalmaer'>Dion Almaer</a></strong><br/>dalmaer</span></span></p></div> <!-- end of tweet -->

<br/>I'm in the area and not going to let the opportunity pass. So here I am.

PPK, Quirks man that he is, explains that the mobile web is more exciting than desktop these days. Twenty browsers and counting! But beyond the proliferation of browsers to pore into, mobile matters. Eventually around five times the number of desktop users in PPK's estimate.

Luke Wroblewski invented the "Mobile First" mantra. The mobile constraint forces you to design lean. Even a big screen is 480*360...that's what you get to deal with, and any fluff sends them right to your competitor. Consider a news site. All you see is headlines. Funny about that, it's all you really need.

<h3>On Mobile Browsers</h3>

PPK lists a plethora of mobile browsers and asks, "Do you have to test on each of these?". Answer: "In theory, yes. In practice, don't be silly." PPK continues to drive his message that there's "no" mobile WebKit. Witness the comparison of mobile WebKits at http://quirksmode.org/webkit.html.

It's important to be aware of the Proxy Browsers, namely: Opera Mini (not Opera Mobile), Ovi (upcoming from Opera), Bolt, and UCWeb. With these browsers, a highly compressed image is sent to the client, and this actually has two (potential) benefits: less network cost and less device requirement. However, once you get fancy with client-side scripting, these devices won't do much at all. It's just not what they're made for.

<h3>The Stattage</h3>

Time for some stats. According to StatCounter, in Q4, 2010:

* Safari: 23% 
* Opera: 22% 
* BlackBerry: 18% and dropping
* Nokia: 16% 
* Android: 12% and growing fast
* NetFront 4% (on basic Sony Ericsson and Samsung)
* Samsung 1% (on Bada)

MS doesn't feature here because many manufacturers introduce Opera (or other) instead of relying on the default IE browser. Interestingly, the Bada browser was met approvingly when PPK showed it to folks recently, and does well in performance.

It's important to be aware of your own stats  and circumstances too, e.g. PPK noticed, for his site at least, social media referrals cause disproportionate queries from iPhone and Android. So people dependent on social media should think about those.

PPK says right now, the browsers for most developers to consider, are Safari iPhone, Opera Mini, and Android Webkit. Beyond that, it depends on geography. In the US, BlackBerry is next to consider. Unfortunately, a recent stat said 90% of BlackBerry users are still on 5.0 or older, ie no WebKit and a very quirky browser. In Europe, Nokia WebKit matters more. Beyond that, Dolfin for bada and Opera Mobile are worth considering; fairly low mobile share, but pretty easy if the others worked.

<h3>"Mobile gives us the opportunity to practice what we preach when we talk about web standards"</h3>

We all talk about progressive enhancement, but who actually uses it? Again, mobile forces your hand! Basic JavaScript, to augment your semantically sweet HTML, is fine. But advanced - Ajax requests and beyond - may not, so think of progressive enhancement as a spectrum. Also, remember Ajax reuests go over the network, so they can slow things right down and require caution.

PPK argues for feature detection where possible, but experienced developers say browser detection is the only way in some cases.

<h3>The Future of Apps</h3>

HTML5 is not just a technology that runs in the browser, but one that powers apps. This is a conversation PPK just about <a href="http://www.quirksmode.org/blog/archives/2009/11/apple_is_not_ev.html">kicked off </a> a couple of years ago, and recent trends have begun to vindicate this view. Plugs for http://apparat.io and http://build.phonegap.com from PPK right about now.

<h3>PPK Questions the Future of App Marketplaces</h3>

Right now, the proverbial developing-national fisherman might pay $25 for a Nokia feature phone.  Stuff is changing. This year, we'll probably get $75 Android phones, says PPK. Too much for the fisherman right now. But give it a few years and the fisherman's phone is running apps. Is he using a marketplace? Right now, those mostly require credit cards, so what happens? Download from the net? Too expensive.

So this is where PPK talks about transferring apps device-to-device. The apps are transferred by bluetooth or NFC and the data transferred with JSON-over-SMS. PPK says it's hard right now to transfer via bluetooth on newer phones, where it works fine on future phones. The end of app stores is a consequence of this vision, sharing <a href="http://twitter.com/meyerweb/status/11847826713">Eric Meyer's quote</a>: "Why is everyone so exercised? As with all walled gardens, the web will interpret the App Store as damage and route around it."

(MM - This opens up a lot of security concerns.)

Why does PPK think the marketplaces won't work for all the platforms in the long term?
* Discoverability - worked in the past, but is harder in a more cluttered environment.
* Distribution - the web works just as well or better for distribution
* Works for Apple - it's proven that the average Apple consumer will spend money on Apple. PPK argues Google has more leverage with developers than consumers. He says that's the opposite for Nokia, Samsung, and RIM - in his theory, they have high leverage with consumers and low leverage with developers.
* Cost of Ownership - Marketplaces need payment systems, sysadmins, content checkers, documentation and best practices writers, and they cost money.

PPK notes there's a problem with Device APIs right now, i.e. users are prone to "Yes" everything. He notes there's a UI issue with modal dialogs - users will say yes! Specs are BONDI, JIL, DAP, and WAC 2.0.