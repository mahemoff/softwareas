---
id: 1885
title: Private resources with ElasticSearch and Tire
date: 2013-01-22T04:07:59+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1885
permalink: /private-resources-with-elasticsearch-and-tire/
categories:
  - SoftwareDev
tags:
  - ElasticSearch
  - Rails
  - Tire
---
I'm adding private channels to [Player FM](http://player.fm) and one consideration is search results. [Tire's activerecord](https://github.com/karmi/tire) does a great job at making updates transparent, but in this case some manual overriding is required.

<script src="https://gist.github.com/4591922.js"></script>

Importantly, this allows the user to switch privacy on and off, and the index will automatically be created and deleted. I initially considered using a "_changed?" check, but realised it's unnecessary as ElasticSearch's `remove` operation is [idempotent](http://en.wikipedia.org/wiki/Idempotence). In other words, it's safe to remove an already-removed item. Yes, the call could be avoided by checking if the resource is already private, but the call is cheap, a fraction of the cost incurred if the channel was public anyway (i.e. it would have to be re-indexed).

There was [some talk of a "should_be_indexed?" method](https://github.com/karmi/tire/pull/115) which any record could override. I think it would be perfect for this use case - it'd just be a case of a one-word return value (`public?`) but alas, it wasn't added. As the code above shows, though, it's pretty simple to DIY.

<a href='http://www.flickr.com/photos/zebble/6080622/'><img src='http://farm1.staticflickr.com/7/6080622_bd95d499a5_z.jpg'></a>
[image by Zebble](http://www.flickr.com/photos/zebble/6080622/)