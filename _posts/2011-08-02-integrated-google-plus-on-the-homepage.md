---
id: 1270
title: Integrated Google Plus on the Homepage
date: 2011-08-02T12:40:40+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1270
permalink: /integrated-google-plus-on-the-homepage/
dsq_thread_id:
  - "375137661"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Feeds
  - Google
  - GooglePlus
  - PHP
  - RSS
  - Social
---
I'm getting more convinced <a href="http://news.ycombinator.com/item?id=2836540">Plus is the new Twitter</a>, and also the new Posterous. I've been posting things on there I previously would have stuck on the Twitter or the Posterous, and so it was time to integrate Plus on my homepage alongside the existing Twitter and Posterous links.

<img src="http://farm7.static.flickr.com/6005/6001773652_d7928674dc.jpg" />

<h3>Latest Post</h3>

It was pretty easy to integrate my latest Google Plus post (we don't really have a name for a Plus post yet; a plust?), as I already have a framework in place for showing the last post from an Atom or RSS feed.

First, I found my Plus feed URL thanks to <a href="http://www.russellbeattie.com/blog/">Russell Beattie's</a> <a href="http://plusfeed.appspot.com/">unofficial Plus Atom Feed</a> service:

http://plusfeed.appspot.com/106413090159067280619

Using MagpieRSS, you can easily get the last post.

[php]
  define('MAGPIE_CACHE_ON', false);
  require_once('magpierss/rss_fetch.inc');
  $feed = "http://plusfeed.appspot.com/106413090159067280619";
  try {
    $rss = fetch_rss($feed);
    $recent_post = $rss->items[0];
    $title = $recent_post[title] . " ...";
    $link = "http://mahemoff.com/+", $recent_post[link];
    $timeAgo = timeAgo(strtotime($recent_post[updated]));
    // show the post
  } catch(Exception $ex) {
    // log exception
  }
[/php]

<h3>Me</h3>

Inside the CSS3-rendered vcard, there's a link to my plus alongside twitter etc.:

[html]
<a rel="me" class="url" href="https://plus.google.com/106413090159067280619">plus</a>
[/html]

<h3>/+ .... redirect to Plus</h3>

Following <a href="https://plus.google.com/107606703558161507946/posts/Jg4p7ivATCn">Tim Bray's suggestion</a>, I redirected http://mahemoff.com/+ to the plus page. It's nice to have a memorable URL.