---
id: 908
title: 'Another HTML5 Tidbit: Web SQL Database'
date: 2010-05-27T22:10:04+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=908
permalink: /another-html5-tidbit-web-sql-database/
dsq_thread_id:
  - "375149428"
categories:
  - SoftwareDev
tags:
  - html5
  - Javascript
  - offline storage
  - Web
  - Web SQL Database
---
I coded up a <a href="http://project.mahemoff.com/sql.html">small demo of Web SQL Database</a>. As the demo points out, notice you can hit reload and the data remains, being that it's one of the several techniques for offline storage.

There's not much to say about Web SQL - you either know SQL already, in which case it's fairly straightforward and just a matter of squeezing your SQL calls into the conventions of the API, like any other SQL framework as, lamentably, there's never been any kind of standardisation on the wrappers that go around SQL - or you don't know SQL, in which case there's your bottleneck child if you intend to use Web SQL Database for offline storage.

<a href="http://dev.w3.org/html5/webdatabase/">Web SQL Database</a> lies at the other end of the complexity spectrum from <a href="http://dev.w3.org/html5/webstorage/">Web Storage</a> (aka localStorage and sessionStorage), which is simply a big ol' hashmap for your domain. The complexity is fairly manageable, though, as there's literally a generation of SQL know-how out there, and hopefully ActiveRecord-like libraries on their way.

<a href="http://www.w3.org/TR/IndexedDB/">IndexedDB</a> promises to offer a third way - more like the hashmap approach, but with some of the indexing-based performance gains SQL has to offer. No browsers have implemented it yet, though you can build an experimental windows version using a third-party <a href="http://code.google.com/p/indexeddb/wiki/build">Firebreath implementation</a>.