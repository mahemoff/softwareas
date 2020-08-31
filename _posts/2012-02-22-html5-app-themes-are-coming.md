---
id: 1515
title: HTML5 App Themes Are Coming
date: 2012-02-22T11:53:54+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1515
permalink: /html5-app-themes-are-coming/
categories:
  - SoftwareDev
tags:
  - boilerplate
  - bootstrap
  - html5
  - themes
---
There are plenty of [premium theme markets](http://www.wordpress-templates.com/top-10-theme-sites/) out there. Many are for vanilla websites, where they provide you with the entire HTML, CSS, and JavaScript, while some are for specific frameworks, e.g. [WordPress themes](http://templatic.com/) aplenty.

A huge gap in the market remains: Apps. Having trawled through a bunch of these &mdash; admittedly some months ago &mdash; I concluded the closest thing was some system admin templates for systems like CPanel. Yet every day, hobbyists and startups are creating thousands of apps. Not on the same scale as marketers are churning out WordPress blogs about &lt;insert-niche-here&gt;, but still, big enough to warrant art-less developers not having to cobble together their own look-and-feel for a v1.

A big part of the problem is lack of standardisation. HTML5 apps pretty-much have any arbitrary page structure and class names. The HTML5 semantic tags may have helped here to standardise on entities like "section" and "article", but it's not clear how many developers are using those elements. And I'm sure some, like me, are just using them as class names for divs (for improved compatibility), while others are using the actual tags, and some are doing the Right Thing by using both. Where WordPress themes can assume a lot about page structure, HTML5 app frameworks cannot.

In other words, HTML5 suffers from a lack of conventions. WordPress is not the only example of the power of conventions. Witness the vibrant marketplace of Rails gems, which can support powerful styles of reuse because they are able to build on conventions. Likewise, jQuery and Backbone plugins.

This will change soon because of two great frameworks: [Twitter Bootstrap](http://twitter.github.com/bootstrap/) and [HTML5 Boilerplate](http://html5boilerplate.com/). These are becoming very common frameworks for HTML5 developers to get started and will soon be combined if [this issue](https://github.com/h5bp/html5-boilerplate/issues/936) happens with Boilerplate 2.5. It will build a Bootstrap kickstart for Boilerplate. That's a real Bootstrap.

![](http://i.imgur.com/sd8hS.jpg)

You can start to see Bootstrap apps sprout like weeds across the web, marked by their characteristic Twitter-like black navbar. It's a genius framework and one I've benefitted from immensely. But the problem is, for something called Bootstrap, it surprisingly doesn't include any HTML at all. So that navbar is actually what people are mostly cut-and-pasting from the docs and examples. The lack of standards makes it hard to produce themes. There's already a [premium theme site](http://wrapbootstrap.com/) out there, but it proves my point. If you look at the markup, it's wide and varied, even for the navbar.

I'm hopeful the Boilerplate combination will rectify that situation. If apps can move towards a common page structure and naming conventions, a world of themes will blossom.

![Imgur](http://i.imgur.com/DCXDR.png)