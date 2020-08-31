---
id: 510
title: Google jQuery CDN
date: 2009-01-22T14:12:01+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=507
permalink: /google-jquery-cdn/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375145517"
categories:
  - SoftwareDev
tags:
  - Ajax
  - CDN
  - Google
  - JQuery
---
NO LONGER UPDATED: July 2012. This page is no longer indexed prominently in Google, so keeping it up-to-date is not much use to anyone. So consider updates finished.
[Try this link instead](http://docs.jquery.com/Downloading_jQuery#CDN_Hosted_jQuery)

SUMMARY: Get the latest jQuery here:

<a href="http://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js">http://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js</a>

To include in your web app, cut-and-paste this:

&lt;script src="http://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"&gt;&lt;/script&gt;

You can also cut-and-paste one of the following to suck it down:

* curl -O http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js
* wget http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js

----

With the release of JQuery 1.3, I thought I'd mention the Google JQuery CDN, one of several libraries you can yoink from Google's <a href="http://code.google.com/apis/ajaxlibs/">Ajax Libraries API</a>. Instead of hosting your own JQuery, you just point your web app to Google's JQuery:

&lt;script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js"&gt;&lt;/script&gt;
(Modified version from 1.3. I'll try and keep this post linking to the latest version.)

Google's documentation would lead you to believe you need to import Google's library, and then call <tt>google.load()</tt>, but it's unnecessary; just pull in the script directly using the link above. The link is officially documented, so it's going to stay put for a very, very, long time.

There are also other libraries available on Google's CDN and <a href="http://dev.aol.com/dojo">elsewhere</a>.

The main point of the CDN is caching. If a user hits 100 JQuery sites, the library will only be downloaded once, and the remaining 99 sites will pull it from the local cache. From an operation cost, you also get to offload the cost of server Javascript to Google. As an added bonus, I also find it easier as a developer to kick off a new project by just linking to the CDN - no need to download and copy the latest version of JQuery.

Great. So when not to use a CDN?

Obviously, whenever you're working offline. This sometimes occurs as a developer working locally, and with <a href="http://code.google.com/p/trimpath/wiki/SinglePageApplications">Single Page Applications</a> like <a href="http://tiddlywiki.com">TiddlyWiki</a>. (The next "major minor" release of TiddlyWiki, v2.5 is JQuery-powered.)

Another case would be when you can deliver faster than the CDN, and care about that. This might be the case when all users are close to the server. Even then, though, you won't get the local cache benefit from users who already have the JQuery.

Finally, privacy and security concerns. Using the CDN, you are trusting the CDN to faithfully serve JQuery and relying on no third-parties injecting funniness in between the CDN and your user's browser. If anything went wrong here, your user could be subject to a world of XSS and CSRF attacks. Or, in a more mundane scenario, the CDN might simply go down, thus breaking your web app. Furthermore, you're giving the CDN data about your users this way. Although Google doesn't use cookies, others might; and even if they don't, the IP number is going to be sent back to them. The referrer - being your website - will also be sent to them, so they can, if they want, track your website's usage.

For many websites, though, it's great that we can use a reliable CDN like Google's to fetch JQuery fast.

Update (11-Feb-2009): In a show of recursive linking, I should fess up as to <a href="http://twitter.com/mahemoff/status/1199810558">why I originally sat down to wrote this</a> ...
<a href="http://twitter.com/mahemoff/status/1199810558"><img style="width:400px;" src="http://img.skitch.com/20090211-bhd9kuhk1tdanbmf24bbhihh1x.jpg" alt="twitter message" />.</a>

Update (erm, mid-2009 sometime): Montana left a comment pointing out you can also drop off the minor numbers to get the latest version. So, for the latest JQuery (since 2.0 doesn't exist), use http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js. Or, for the latest in the old 1.2 series: http://ajax.googleapis.com/ajax/libs/jquery/1.2/jquery.min.js.

Update (19-March-2010): Scratch that. @premasagar pointed out to me that the link to just the latest version  (until 2.0, i.e. http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js) as opposed to a specific version (http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js) is undesirable; <a href="http://nichol.as/how-google-is-wasting-your-bandwidth">Google will expire the "latest" content after one hour</a>, as opposed to one year for a specific version. This is for good reason of course, as the latest version is subject to change. For this reason, I've reverted the link at top to be a specific version, which I'll endeavour to update upon each new release.