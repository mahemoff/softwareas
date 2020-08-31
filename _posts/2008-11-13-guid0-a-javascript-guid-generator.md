---
id: 494
title: 'Guid0: A Javascript GUID Generator'
date: 2008-11-13T13:15:42+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=491
permalink: /guid0-a-javascript-guid-generator/
dsq_thread_id:
  - "375251772"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Guid0
  - Javascript
  - TiddlyWiki
---
<a href="http://mahemoff.com/project/guid0/guid0.js">Guid0.js</a>

Guid0 is a GUID library for Javascript. Okay, it doesn't yet do official, bona fide, 128-bit, GUIDs yet, mainly for API design reasons. But this is a library you might find useful if you want to generate a unique ID in your Ajax app.

Usage:

[javascript]
guid = new Guid();
guid.generate(); // Returns a unique ID, e.g. "dkvagrkx1rt"
[/javascript]

With options:

[javascript]
guid = new Guid(
  {
    chars: Guid.constants.base85,  // or you could say "abc" if you only wanted those chars to appear
    epoch: "June 1, 2003",
    counterSequenceLength: 2, // a counter field appended to the end
    randomSequenceLength: 2 // a random field appended to the end
  }
)
[/javascript]

The demo:

<a href="http://mahemoff.com/project/guid0/"><img src="http://img.skitch.com/20081113-tx2xfu9jcchf5xd6f86g8pua9t.jpg"></a>

The demo generates a bunch of GUIDs. They look almost the same because most of the GUID is just a time representation in Base N (where N is the number of characters in the GUID's configured charset).

I made Guid0 in conjunction with <a href="http://tiddlywiki.com">TiddlyWiki</a> work. Within a store, tiddlers are keyed on their title. In the typical case, the user has entered a title to describe the content. But when we get into application territory - <a href="http://softwareas.com/reflections-from-a-tiddlywiki-tiddler-and-thoughts-on-a-guide-for-web-app-development-with-tiddlywiki">using TiddlyWiki as an application framework</a> - there are reasons why we want the more familiar database approach of automagically generating the primary key. These are several reasons for this:

* Tiddlers with no meaningful title. Sometimes, tiddlers are just containers for text someone has entered. A perfect example is the Comments Plugin I've been working on (separate blog post pending). A comment is a tiddler. When you have a blog or forum or whatever with comments, you usually don't invite users title their comment...it's not very enticing. So in this case, the comment is the tiddler text and the title must be auto-generated so we can put it in the store.
* Renaming. As with the usual motivation for auto-generated IDs over meaningful IDs, renaming support is sometimes required. In one case, I have a user submitting a first cut of something, and an admin coming along later and cleansing it. We can't expect the user to get the name right the first time, and there are several tiddlers referencing the initial tiddler (via custom fields) by the time it might be renamed.
* Can't ensure uniqueness. With multiple users, you don't always want to force them into choosing different titles for each tiddler. If the comments plugin *did* include titles for instance, you wouldn't want a uniqueness constraint. Using GUIDs, you could support multiple titles with the same display name.

The library is generic - not TiddlyWiki-specific - but I've wrapped it into a small TiddlyWiki plugin. In the future, we may expand the plugin. For example, each time a new tiddler is created, the plugin may intercept the call and give the tiddler a GUID title, and stick the title in a "name" field.

I'll update this post when proper 128-bit GUID is supported.