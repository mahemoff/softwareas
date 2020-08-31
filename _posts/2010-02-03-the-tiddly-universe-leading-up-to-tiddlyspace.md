---
id: 778
title: 'The Tiddly* Universe Leading Up to TiddlySpace'
date: 2010-02-03T18:35:46+00:00
author: admin
layout: post
guid: http://softwareas.com/the-tiddly-universe-leading-up-to-tiddlyspace
permalink: /the-tiddly-universe-leading-up-to-tiddlyspace/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375335489"
categories:
  - SoftwareDev
tags:
  - Osmosoft
  - tiddlyweb
  - TiddlyWiki
  - TiddlyWiki MU
---
There have been a dizzying array of Tiddly* products spun off recently. I'm talking merely about the core infrastructure stuff rather than applications like <a href="tiddlypocketbook.com/">TiddlyPocketBook</a>. We're starting to get some convergence within the team, as we're working on a high-level product called TiddlySpace. It's basically the manifestation of <a href="http://softwareas.com/multi-user-tiddlywiki">earlier discussion too.</a>the ideas we were discussing earlier</a>. Similar to WordPress MU or Wikia, you'll be able to spin off new TiddlyWikis at the click of a button. The server itself is open source, so you can host it in your own enterprise or on your own server. And because TiddlyWiki is nowadays an application framework, not just a wiki thing, spinning off new instances means composing new applications.

Pretty much all the applications we're working on right now are intended to run on this infrastructure. Many will run in standalone, file-based TiddlyWiki, as well; i.e. the whole server-sidedness and user authorisation is a completely separate deployment concern. Which is an awesome way to develop. I recently realised we're about the only people in the world who primarily develop file:// based web apps! That they will magically work as multi-user, server-hosted, apps too is certainly a boon for the Tiddly* model.

Anyway, what are all these Tiddly* products Osmosoft's been working on, and how do they lead up to TiddlySpace? Below is the universe of products we've been working on - if all this seems horrendously complicated at first glance, <strong>note that most users will only ever see one thing: either TiddlyWiki or TiddlySpace, and even that may be invisible to them if they are using certain high-level applications. Here, I'm just describing the various components we're working on to pave that path. It'll all be nice for users. Trust.</strong>

<a href="http://www.tiddlywiki.com/">TiddlyWiki</a> - This is the original client UI. It's a web app fitting inside a single HTML file - HTML, CSS and Javascript all together. It can run on a file:/// URI, which means you can store TiddlyWikis on your local drive, a USB drive, or a share drive ... or a http:// URI. In the former case, thanks to some very clever and still-obscure browser hacks, you can make edit the TiddlyWiki and save changes. TiddlyWiki is, at its heart, a personal scrapbook, where you can easily gather and manage free-form bits of content ("tiddlers"). However, some of these bits can include CSS or Javascript, meaning that you can actually start building powerful applications with it and using the underlying tiddlers as a kind of scaffolding. These applicatons can be useful for individuals, but we're still limited to a single user working on their own hard drive. Hence the need for server-side products (see below).

<a href="http://www.tiddlywiki.com/tiddlywiki5/">TiddlyWiki 5</a> - This is a major in-progress upgrade of TiddlyWiki, a complete rewrite, the biggest overhaul in its 5 year existence. There are some much-requested features: follows graceful degradation principle so that the TiddlyWiki5 presents nicely to search engine bots and users with Javascript turned off; includes rich text editing control; SVG graphics; embedded images (with the IE6-compatible MHTML hack);  better readiness for server-side integration (e.g. the possibility to track revisions). And yes, all of this in a single HTML file.

<a href="http://tiddlyweb.com">TiddlyWeb (low-level)</a> - This is new RESTful server-side component we've been building at Osmosoft for persistence, where each Tiddler has its own URI; it's similar to CouchDB and other NOSQL frameworks; the main difference is it provides extreme flexibility on all manner of things like authentication and storage and presentation formats, and will mostly be invisible to users as we're building higher-level abstractions on top of it. Also, the underlying data model is that of tiddlers, which means a title, text, list of tags, creation/modification info, and key-value fields (many NOSQL frameworks will have similar document models, but none exactly matching the Tiddler data structure that has always been present in the TiddlyWiki client UI). For most people, TiddlyWeb is best considered as a powerful component further down the stack than what you actually interact with. You'd only need to know about it in detail if you were trying to do powerful admin things, or change the code, on something higher-level like TiddlySpace; or if you wanted to build something equivalent to TiddlySpace; or you were trying to use it in a kind of NOSQL server capacity.

<a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers/TiddlyWebWiki">TiddlyWebWiki (low-level)</a> - This is a set of plugins for TiddlyWiki that help it talk to TiddlyWeb. It "hijacks" (intercepts) calls like store.saveTiddler() so that instead of saving to the local drive, it will upload to the TiddlyWeb server.

<a href="http://hoster.peermore.com">TiddlyHoster and TiddlyConsole</a> These products will probably converge. TiddlyHoster is a first-cut at the TiddlySpace concept, an inspiring product mostly built by @cdent and cobbling together various plugins. You can try it out now at <a href="http://hoster.peermore.com">http://hoster.peermore.com</a>. It's a fairly direct exposure of the TiddlyWeb bags and recipes model. TiddlyConsole (formerly TiddlyRecon) is similarly a bag and recipe and user mangement tool, with more emphasis on admin usage than that from end-users. We hope the essence of these tools can be incorporporated into TiddlySpace to support power users.

<a href="http://tiddlyspace.com">TiddlySpace</a> - This is a higher-level web app, building on TiddlyWeb, to make it easy for folks to spin off new multi-user (or single-user) TiddlyWiki instances. This is really the most important piece, and the one everything's been leading up to, when it comes to Osmosoft's mission to get all manner of web apps running inside the enterprise, and will hopefully be just as useful for other enterprises as well as ad hoc groups working on the broader internet. With TiddlySpace, you have an application running at http://TiddlyPocketBook.TiddlySpace.com for example. You click a "clone" button, type in "CameraGuide", and suddenly you have a clone of that web app running at http://CameraGuide.TiddlySpace.com. The neat thing is that the new space has copies of all the pocketbook tiddlers, which you can happily hack. The application tiddlers are "copied by reference" from a master application space, say http://TiddlyPocketBookApp.TiddlySpace.com, so you will inherit any future changes made to the application. All this sounds complicated, but will be seamless to the user, and is also easy for us to implement while building TiddlySpace, thanks to TiddlyWebs' flexible bags and recipes model for containment of tiddlers. (See my <a href="http://softwareas.com/multi-user-tiddlywiki">earlier discussion too.</a>) Pretty much all of TiddlySpace is driven by client-side code TiddlyWiki plugins, connecting to the TiddlyWeb server.

We've spent a while talking about the design of TiddlySpace and tomorrow we have a hackday with the goal of getting a v0.1 running. 