---
id: 538
title: 'As We May Think: URL Trails'
date: 2009-05-20T10:27:32+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=535
permalink: /as-we-may-think-url-trails/
dsq_thread_id:
  - "375574224"
categories:
  - SoftwareDev
tags:
  - Im8ge
  - Osmosoft
  - trails
  - Web
---
<img src="http://picupper.com/2009/05/20/3142693919_702d674a55.jpg" style="width: 400px;" />

<a href="http://www.theatlantic.com/doc/194507/bush">As We May Think</a>, Vannevar Bush's legendary paper presaging hypertext, wikis, and the web, penned in 1945. Many features of his ficticious "memex" device have come to fruition on the web, but one thing I always find lacking is his concept of trails:

> When the user is building a trail, he names it, inserts the name in his code book, and taps it out on his keyboard. Before him are the two items to be joined, projected onto adjacent viewing positions. At the bottom of each there are a number of blank code spaces, and a pointer is set to indicate one of these on each item. The user taps a single key, and the items are permanently joined. In each code space appears the code word. Out of view, but also in the code space, is inserted a set of dots for photocell viewing; and on each item these dots by their positions designate the index number of the other item.

> Thereafter, at any time, when one of these items is in view, the other can be instantly recalled merely by tapping a button below the corresponding code space. Moreover, when numerous items have been thus joined together to form a trail, they can be reviewed in turn, rapidly or slowly, by deflecting a lever like that used for turning the pages of a book. It is exactly as though the physical items had been gathered together from widely separated sources and bound together to form a new book. It is more than this, for any item can be joined into numerous trails.

> The owner of the memex, let us say, is interested in the origin and properties of the bow and arrow. Specifically he is studying why the short Turkish bow was apparently superior to the English long bow in the skirmishes of the Crusades. He has dozens of possibly pertinent books and articles in his memex. First he runs through an encyclopedia, finds an interesting but sketchy article, leaves it projected. Next, in a history, he finds another pertinent item, and ties the two together. Thus he goes, building a trail of many items. Occasionally he inserts a comment of his own, either linking it into the main trail or joining it by a side trail to a particular item. When it becomes evident that the elastic properties of available materials had a great deal to do with the bow, he branches off on a side trail which takes him through textbooks on elasticity and tables of physical constants. He inserts a page of longhand analysis of his own. Thus he builds a trail of his interest through the maze of materials available to him.

> And his trails do not fade. Several years later, his talk with a friend turns to the queer ways in which a people resist innovations, even of vital interest. He has an example, in the fact that the outraged Europeans still failed to adopt the Turkish bow. In fact he has a trail on it. A touch brings up the code book. Tapping a few keys projects the head of the trail. A lever runs through it at will, stopping at interesting items, going off on side excursions. It is an interesting trail, pertinent to the discussion. So he sets a reproducer in action, photographs the whole trail out, and passes it to his friend for insertion in his own memex, there to be linked into the more general trail.

Now at one level, any web page is a trail. Thanks to the magic of hypertext, any website is effectively a view onto the rest of the web, with the author being able to list links and comment on them. However, I don't find much in the way of explicit support for this concept of trails.

Basically, I see a trail as a linear sequence through a bunch of resources, with the potential to annotate at each step. On the web, a resource is represented as a URL, so assuming everyone <a href="http://blog.whatfettle.com/2008/10/06/the-uri-is-the-thing/">plays ball</a>, building a trail is as simple as building a list of URLs, with some form of annotation for each. That's the nice thing about URLs - it doesn't matter if it's a written article, a photo, or a video; they are all URLs. Furthermore, it doesn't even have to be served via http; it could be a file on your hard drive (file:), an email adress (mail:), or an IRC channel (irc:). They can all live together in harmony in the same trail.

The closest popular thing I've seen to this is Amazon's <a href="http://www.amazon.com/gp/richpub/listmania/toplists">ListMania</a>. My favourite ones are those beginning with "So you ..." as in <a href="http://www.amazon.com/So-nbsp-You-nbsp-Want-nbsp-To-nbsp-Be-nbsp-A-nbsp-Geologist/lm/3W1787F9CA7GB/ref=cm_srch_res_rpli_alt_18">So you want to be a geologist</a> or <a href="http://www.amazon.com/So-nbsp-you-nbsp-like-nbsp-to-nbsp-read-nbsp-about-nbsp-the-nbsp-Trojan-nbsp-War/lm/R2QW17V4U4F82V/ref=cm_srch_res_rpli_alt_13">So you like to read about the Trojan War</a>. These capture the spirit of Vannevar B's tome; as a budding geologist, I might find a book or two on geology and see that list linked from the side, where I can get the (hopefully) expert opinion on the trail I can follow towards mastery.

There is also some interest around <a href="http://en.wikipedia.org/wiki/Outliner">outlining</a>, which is basically the trail concept when taken in a web concept, although you don't see it being a big part of the web explicitly.

I was chatting to <a href="http://jaybyjayfresh.com">Jon</a> last night and he refers to these as tour guides, and pointed me to <a href="http://thenethernet.com">The Nethernet</a>, an unusual "game" that appears on websites you surf, based on Firefox plugins. It includes a concept of a "quest" where you can jump between websites, following a trail laid out by someone else.

All of this has been converging lately with several activities happening at Osmosoft. As a project in my spare time, I've been working on a tool to <a href="http://caption.im8ge.com">caption images</a>. A trail of captioned images would be good as a slideshow. As a project in his spare time, <a href="http://simonmcmanus.com">Simon</a> has been working on an excellent <a href="http://goodtube.me">video player</a>. The player runs through a playlist, which can be populated in various ways. Each of the videos is effectively a URL, so the playlist is effectively a trail. And in <a href="http://tiddlydocs.com">TiddlyDocs</a>, one of our main projects at Osmosoft</a>, a document is a hierarchy of sections, each being a tiddler sitting on a unique (TiddlyWeb-backed) URL. So the document's table of contents is also a trail. <a href="http://jermolene.com">Jeremy</a> realised the implications of this early on, and we've begun talking with him about a richer format for the document spec, so it can include annotations and transitions between items. Note that it's also a hierarchy rather than a list, but that's fine because (a) a list is a subset of a hierarchy, so the scheme we arrive at will be able to degenerate into a list representaiton; (b) a hierarchy can still be traversed in a deterministic, linear, fashion - as you do when you read a book which is composed of sections, subsections, and so on.

So where we're at now is deciding on the format for a trail like this. It will probably be JSON-based and be inspired by OPML at some level. Being a file format which will be baked into people's content, it needs a little more upfront thinking than a coding exercise.