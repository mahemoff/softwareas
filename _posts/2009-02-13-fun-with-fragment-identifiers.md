---
id: 523
title: Fun with Fragment Identifiers
date: 2009-02-13T13:10:49+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=520
permalink: /fun-with-fragment-identifiers/
dsq_thread_id:
  - "375574160"
categories:
  - SoftwareDev
tags:
  - Ajax
  - AjaxPatterns
  - fragment identifiers
  - hash
  - Javascript
  - Web
---
I was recently invited to make a statement on WebMasterWorld about something in advanced Javascript at the edge of my understanding. I decided to cover <a href="http://www.webmasterworld.com/javascript/3843919.htm">fragment identifiers</a>, something I have an odd obsession about:

<blockquote>
<p>There's a lot of cool stuff going on right now, standards-based graphics and sound foremost in my mind. But I'll focus here on something I've always found oddly fascinating: fragment identifiers and the quirky exploits around them. The humble "frag ID" is not exactly the pinnacle of the Ajax revolution, but it remains misunderstood and under-utilised by developers, and a feature which the browsers could do more to support. By design, fragment identifiers do just as their name suggests - they identify fragments of a document. Type in http://example.com#foo, and the browser will helpfully scroll to the "foo" element. However, they can be used for a lot more than that, thanks to peculiarities in the way they are handled by browsers.

<p>Most importantly, by writing Javascript to change the fragment identifier, you're able to update the page URL, without effecting a page reload. This fact alone means - contrary to a popular Ajax myth - you can support bookmarking and history in an Ajax application. Furthermore, fragment identifier information is never sent to the server, unlike the rest of the URL, which leads to some interesting applications related to security and privacy. Another powerful application is interacting between iframes from different domain, something which is theoretically "impossible" in older browsers and tremendously important for embedding third-party widgets on web pages. And when I began working at Osmosoft, I discovered yet another application: providing startup context to web apps, such as TiddlyWiki, which run off a file:// URL...as they're unable to read conventional CGI parameter info.

<p>I first researched this stuff for Ajax Design Patterns in 2005, and at that time, there were only a couple of scattered blog articles on the topic. Today, we can see the pattern in action in various high-profile places such as Google Docs and GMail. When I view my starred documents in the former website, for example, the URL is http://docs.google.com/#trash. That said, many developers still aren't using this feature to its fullest, and library support is somewhat lacking. It's encouraging to see IE8 has a new event for monitoring the fragment identifier, which suggests the story is not over for this rarely discussed property.
</blockquote>

This is certainly a hot topic, if not well understood or covered; shortly after I wrote it, I was amused to see the topic <a href="http://www.techmeme.com/090203/p87#a090203p87">showed up on none less than Techmeme</a>:

<img style="width: 400px;" src="http://img.skitch.com/20090213-qd31gnbuixpy667gxa4kdfq7gt.jpg" alt="Techmeme: Google's new Ajax-powered search results breaks search keyword tracking for everyone (getclicky.com/blog) - FireMoff (-;"/>

The issue here is summarised in my statement: "fragment identifier information is never sent to the server, unlike the rest of the URL, which leads to some interesting applications related to security and privacy". <a href="http://www.techmeme.com/090203/p87#a090203p87">These bloggers</a> had noticed that google was (in some cases) changing their URL structure for searches to use hashes (#q=term) instead of traditional CGI params (?q=term). Thus, when the user clicks through from Google to your web page, you don't know what the user searched for.

Another thing that recently arose is how easily you can retain fragment identifiers in bookmarking type sites. For example, if you submit a URL to Digg, it annoyingly strips the fragment ID. Whereas Delicious retains it. TinyURL retains it too, but their php "create" script removes it, according to a conversation I had with <a href="http://fnd.lewcid.org/blog/archive/16">Fred, who created this tinyURL bookmarklet</a>. I can see why sites wouldn't want to retain it, because it may well be just an in-page link, so it's a tricky issue.

The main point being, fragment IDs - and design questions thereof - are alive and well.