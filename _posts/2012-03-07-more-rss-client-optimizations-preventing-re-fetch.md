---
id: 1562
title: 'More RSS Client Optimizations: Preventing Re-Fetch'
date: 2012-03-07T11:14:07+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1562
permalink: /more-rss-client-optimizations-preventing-re-fetch/
categories:
  - SoftwareDev
tags:
  - Feeds
  - HTTP
  - RSS
  - Ruby
---
### Background: Has the Feed Changed?

I [previously](http://softwareas.com/firefighting-an-rss-aggregators-performance) mentioned some work I did to cut down processing and IO on an RSS client. Yesterday, I was able to continue this effort with some more enhancements geared around checking if the feed has changed. These changes are not just important for my server's performance, but also for being a good internet citizen and not hammering others' machines with gratuitous requests. Note everything in this article will be basic hygiene for anyone whose written any kind of high-scale bot, but documenting here as it was useful learning to me.

Normally, a fetch requires the client to compare the incoming feed against what has been stored. This requires lookup on the database and a comparison process. It's read-only, so not hugely expensive, but does require reading a lot &mdash; all items in the feed &mdash; and at frequent intervals.

All this comparison effort would be unnecessary if we could guarantee the feed hasn't changed since the last fetch. And of course, most of the time, it won't have changed. If we're fetching feeds hourly, and the feed changes on average once a week, then we can theoretically skip the whole comparison 99.4% of the time!

So how can we check if the feed has changed?

### Feed Hash

The brute-force way to check if the feed has changed is to compare the feed content with the one we received last time. We could store the incoming feed in a file, and if it's the same as the one we just sucked down, we can safely next it.

Storing a jillion feed files is expensive and unnecessary. (Though some people might temporarily store them if they've separated the fetching from the comparison, to prevent blockages, which I haven't done here). If all we need the files for is a comparison, we can instead store a hash. With a decent hash, the chance of a false positive is extremely low and the severity in this context also extremely low.

So the feed now has a new hash field.

[ruby]
incoming_feed = fetch_feed(feed_record.url)
incoming_hash = Digest::MD5.hexdigest(incoming_feed.body)
return if incoming_hash == feed_record.hash # Files match, no comparison necessary

feed_record.title = incoming_feed.title
feed_record.hash = incoming_hash # Save the new hash for next time
# ... Keep processing the feed. Compare each item, etc.
[/ruby]

### HTTP if-not-modified-since

The HTTP protocol provides its own support for this kind of thing, via the if-not-modified-since request header. So we should send this header, and we can then expect a 304 response in the likely event no change has happened. This will save transferring the actual file as well as bypassing the hash check above. (However, since this is not at all supported everywhere, we still do need the above check as an extra precaution.)

[ruby]
req = Net::HTTP::Get.new(feed_record.url)
req.add_field("If-Modified-Since", last_fetched_at.rfc2822) if last_fetched_at
...
res = Net::HTTP.new(...)
return if res.code=='304' # We don't even need to compare hashes
[/ruby]

### ETag

Another HTTPism is ETag, a value that, like our hash, is guaranteed to change if the feed content changes. So to be extra-sure we're not re-processing the same feed, and hopefully not even fetching the whole feed, we can save the ETag and include it in each request. It works like if-not-modified-since; if the server is still serving the same ETag, it will respond with an empty 304.

[ruby]
req.add_field("If-None-Match", etag) if etag
...
# Again, we return if res.code=='304'
feed_record.etag = incoming_feed.etag # Save it for next time
[/ruby]

For the record, about half of the feeds I've tested &mdash; mostly from fairly popular sources, many of them commercial &mdash; include ETags. And of those, at least some of them change the ETag unnecessarily often, which renders it useless in those cases (actually worse than useless, since it consumes unnecessary resources). Given that level of support, I'm not actually convinced it adds much value over just using if-not-modified-since, but I'll leave it in for now. I'm sure managers of those servers which do support it would prefer it be used.

<a href='http://www.flickr.com/photos/psd/421186578/sizes/o/in/photostream/'>![](http://farm1.staticflickr.com/149/421186578_fbb062368e_o.jpg)</a>