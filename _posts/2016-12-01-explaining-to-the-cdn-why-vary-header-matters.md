---
id: 2264
title: 'Explaining to the CDN why &#8220;vary&#8221; header matters'
date: 2016-12-01T14:29:59+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2264
permalink: /explaining-to-the-cdn-why-vary-header-matters/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"c1654796de1d";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:41:"https://medium.com/@mahemoff/c1654796de1d";}'
categories:
  - Uncategorized
---
A CDN asked me why they should respect the HTTP "vary" header. My reply was this.

"vary" is needed because the app uses "PJAX" architecture used by many dynamic web apps and embraced in frameworks like Rails' TurboGears. Simply put, all links are "hijacked" so that when the user clicks on them, the server responds with a slimmed-down version of the full page. It doesn't have headers or footers.

It still comes from the same URL, so we have "full pages" and "partial pages" both served with the same URL. If the user enters a URL in their web browser and the CDN responds with a "partial page", it will look like rubbish and fail to function, as there won't be any stylesheets or scripts (as well as missing page headers and footers). And similarly, if the hijack ends up receiving a full page with headers and footers, it causes initial page scripts to be re-executed, leading to bugs and causes memory leaks.

With the CDN ignoring "vary", I've had to hack the client PJAX library to force the URL to change when it's hijacked (appending ?xhr=true). However, it still fails on redirects, as I can't do anything about them on the client side. I added another hack to change it on the server side during redirect, but now people have reported this is still an issue with the homepage, which I can't even track down, so I've now had to turn off caching on that page and still unsure what other pages are affected. Hopefully, that makes it clear why I'm screening for CDNs which respect the "vary" standard.