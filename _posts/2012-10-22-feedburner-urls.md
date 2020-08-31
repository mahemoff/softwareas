---
id: 1854
title: Feedburner URLs
date: 2012-10-22T12:29:35+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1854
permalink: /feedburner-urls/
categories:
  - SoftwareDev
---
<img src='http://i.imgur.com/SfBAK.png'>

I explained in [the previous post](http://softwareas.com/canonical-feeds) that we need to canonicalise Feedburner URLs. Since about a quarter of the feeds are Feedburner, this is worth special-casing when it comes to parsing rules. Lots of different Feedburner URLs end up floating around for what it actually the same feed. This is partly because feedburner doesn't redirect funny variants. That actually makes sense, since a lot of RSS clients apparently aren't smart enough to handle redirects, believe it or not. Though it wouldn't be altogether insane if they sent in a header the canonical URL. But anyway. It just serves them as happy 200 responses. So the variants end up floating around. So I need to canonicalise the variants to be the same URL. Here's what I've learned.

Update: [Show me the code](https://gist.github.com/3931897)

#### Full Path Matters.

The canonical URL is http://feeds.feedburner.com/<name1>[/name2]. /name2 is optional and rarely use, so most feedburner URLs are http://feeds.feedburner.com/<name>.

For example, a typical name is http://feeds.feedburner.com/TheNerdpocalypse

Sometimes the path is longer, and you can't ignore that full path (ie., /name2). For example, http://feeds.feedburner.com/linuxbasix/mp3 is a podcast feed, http://feeds.feedburner.com/linuxbasix is not. path. http://feeds.feedburner.com/lifestyle-business-podcast doesn't exist, but http://feeds.feedburner.com/lifestylelife/LwyMis hours of listening pleasure.

#### Dulphanumeric

Looking at a big sample, it seems that you're allowed: alphabet, numbers, dash, and underscore. That's an 38 significant characters, given that ...

#### Case doesn't matter

http://feeds.feedburner.com/TheNerdpocalypse and http://feeds.feedburner.com/TheNerdPocalypSe and http://feeds.feedburner.com/thenerdpocalypse are all the same thing. For this reason, I will downcase everything to canonicalise the URL, and consider a second "pretty_url" column if we want to display the feed nicely and in line with the publisher's proclivities.

#### Domain doesn't matter

Sometimes I see http://feeds2.feedburner.com domain. I don't know why this leaks out past Feedburner's farm (or at least, why we don't see hundreds of other domains like that if it does leak out), but it doesn't matter. http://feeds2.feedburner.com/TheNerdpocalypse is the same as http://feeds.feedburner.com/TheNerdpocalypse.  So whenever I see feeds2, it becomes feeds.

#### Slashes don't matter

http://feeds.feedburner.com/TheNerdpocalypse/ is the same as http://feeds.feedburner.com/TheNerdpocalypse.

#### Suffixes don't matter

I also see the dapper .xml or .rss variant, e.g. http://feeds.feedburner.com/TheNerdpocalypse.xml. REST envy perhaps...but the suffix does nothing useful. Ignore.

#### CGI doesn't matter

?format=xml smells like even more REST envy, but afaict it doesn't do anything either. Honeybadger don't care.

#### Bonus factoid: feedproxy *will* redirect

A URL like http://feedproxy.google.com/TheNerdpocalypse will redirect to http://feeds.feedburner.com/TheNerdpocalypse. And this keeps the full path intact, i.e if there's an xml on the end, it will stay on the end after the redirect.

### Summary

I'll use a URL parsing library for this. Lowercase the URL, extract the path without CGI parameters, strip the trailing slash. That will about do it.