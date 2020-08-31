---
id: 2069
title: Server-side rendering of Single Page Apps
date: 2015-02-18T17:47:11+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2069
permalink: /server-side-rendering-of-single-page-apps/
categories:
  - SoftwareDev
tags:
  - Performance
---
In the simplest case, a Single Page App is merely an empty HTML body with JavaScript and template elements used to bring the page to life.

Web developers have begun to re-consider this starting point for SPAs. Even if an empty body tag is digestible by Googlebot and acceptable to screen-readers, there's a performance problem. The quintessential case study is Twitter, who found it's not such a good idea to send and run a megabyte of scripts just to view 140 characters. They [returned to server-side rendering in 2012](https://blog.twitter.com/2012/improving-performance-on-twittercom) to improve their "Time to first tweet" metric.

### Server-side rendering

One approach is [what AirBNB famously calls the Holy Grail](http://nerds.airbnb.com/weve-launched-our-first-nodejs-app-to-product/): running the same NodeJS client on both ends. along those lines, EmberJS is working on [FastBoot](http://emberjs.com/blog/2014/12/22/inside-fastboot-the-road-to-server-side-rendering.html), a way to render on the server, and Tom Dale has [written about it](extensively).

But what if you don't have, or don't want to have, your server-side code base in JavaScript? You could still separate out a web <s>tier</s> microservice (it's the future!) in JavaScript. If you don't want to do that, you could [pre-render](https://github.com/prerender/prerender) every page using a headless browser and build it as a static HTML file. That has the advantage of being super-fast, but requiring a bunch of infrastructure.

### An alternative approach I'm exploring

Wanting to keep my solution lightweight, and not have to run Node on the server or pre-render millions of pages, my plan for [the Player FM website](https://player.fm) is a variant of the old "Dynamic Placeholder" approach where the initial page is served with "holes" in it and the client subsequently makes requests to populate the holes. Instead of serving pages with holes, we could serve the entire page and have the client refresh dynamic content blocks in a way that is as unobtrusive as possible.

It goes like this:

* Serve pages as static assets cached for an hour or so (the length will perhaps depend on the anticipated update frequency).
* Dynamic sections in the page will use a data tag to keep track of timestamps for dynamic content.
* A script tag (at the top of the page) will request the latest timestamp for each dynamic unit.
* If any dynamic block has changed, its new content will be requested. This request will include a timestamp property in the URL, so that the block may be long-cached and should then return quickly.
* To avoid a Flash Of Unwanted Text (FOUT), the page content won't be rendered until the initial freshness check has returned, up to a timeout of a few hundred milliseconds has passed, in which case it will indeed be rendered along with a progress indicator until we get the freshness response and can deal with it.

It's a little convoluted, but should mostly be out of the way once the framework is established. As the site already uses a PJAX approach to loading new pages (ie HTML output from server, but only the changed content), subsequent pages could optionally be served even faster by building on this technique, (i.e. in parallel to requesting the next page's HTML, the framework can also request the relevant timestamps. This assumes we are willing to imbue the framework with upfront details of each dynamic page's structure, an increase in complexity for a further performance boost.)

<img class="" src="https://farm9.staticflickr.com/8325/8114017206_be212b9b0b_b.jpg" alt="" width="1024" height="696" />