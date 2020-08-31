---
id: 1883
title: 'Testing ETags:  A Little Gotcha'
date: 2013-01-07T16:39:19+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1883
permalink: /testing-etags-a-little-gotcha/
categories:
  - SoftwareDev
---
TLDR: ETags have quotes, escape them when issuing requests.

I've been using [HTTPie](https://github.com/jkbr/httpie) to test some conditional caching I've been setting up on a JSON API. It's much more intuitive than Curl, very recommended.

A funny thing about ETags is the values are surrounded by quote marks, unlike most other string-based HTTP header values. (And even better, this being the web, there's much [flexibility](http://gsnedders.com/http-entity-tags-confusion) in implementations, even if the quotes are required by the standard.) So a response looks like:

<pre>
HTTP/1.1 200 OK
...
ETag: "avm3pvp34vpoktcbd18db4c"
Normal-Header: some value
</pre>

Having added conditional caching support on the server, I was now looking forward to reaping the reward and seeing 304s show up client-side. Hustling for the cacheworthy `304 Not Modified` response, I tried this:

<tt><s>http -phH localhost:3000 If-None-Match:avm3pvp34vpoktcbd18db4c</s></tt> (Wrong!)

And I kept getting 200s, meaning a fresh response every time. Server wasn't recognising the value because quotes. So the correct thing to do is:

<tt>http -phH localhost:3000 If-None-Match:"avm3pvp34vpoktcbd18db4c"</tt>

And now the server recognises it as the same ETag. Satisfying 304 is Satisfying.

(Of course, this was working all along in the browser. I figured it might be working because of the other conditional caching mechanism - timestamps (Last-Modified and If-Modified-Since headers) - even though the ETags were apparently different. But it turned out the ETags were indeed right as the browser, unlike me on the command-line, knew how to actually send them.)