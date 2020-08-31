---
id: 545
title: TiddlyDocs, TiddlyCMS, and Permissioning Models
date: 2009-06-11T17:14:33+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=542
permalink: /tiddlydocs-tiddlycms-and-permissioning-models/
dsq_thread_id:
  - "375574244"
categories:
  - SoftwareDev
tags:
  - Javascript
  - Osmosoft
  - TiddlyDocs
  - tiddlyweb
  - TiddlyWiki
---
We're designing a setup for TiddlyDocs (and potentially other "TiddlyCMS"s) where there will be an instance for each group of contributors. This is one TiddlyWeb design pattern, where you say "we all trust each other" (although there are still audit logs!) and so everyone can add, delete, or modify all the content  freely. That is, there is only one content bag accessible to all. Likewise, anyone can append comments. There is still an admin role for setting up config stuffs, which only the admin can change; otherwise, any user could easily perform a phisihing attack, for example. Users also have private bags which they can do what they like with - they could use it for drafts, or for overriding shadow tiddlers setup by the admin in config.

A rough sketch looks like this:

<a href="http://picupper.com/2009/05/28/tiddlyweb-homogeneous-content.png" style="width: 400px; height: 300px;"><img style="width:400px; height: 300px;" src="http://picupper.com/2009/05/28/tiddlyweb-homogeneous-content.png" /></a>

(Some things need fixing, but the overall idea is conveyed.)

I discuss more about this architectural pattern with <a href="jaybyjayfresh.com/">Jon</a> in the following video:

<object width="400" height="300"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=4733832&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=4733832&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><p><a href="http://vimeo.com/4733832">TiddlyDocs Architecture</a> from <a href="http://vimeo.com/user960717">Michael Mahemoff</a> on <a href="http://vimeo.com">Vimeo</a>.</p>

Now that model alone is good enough for basic cases, where you have a group of people who work together and just want to set up an instance. TiddlyWeb handles that just fine, even using the basic cookie authentication technique. In more complex situations (read: "enterprises"), you have a many-to-many relationship between users and instances. I was talking with <a href="http://cdent.tumblr.com/">TiddlyWeb's architect, Chris Dent</a>, about possibilities, and we decided on one possible model:

<p>
<a href="http://picupper.com/2009/06/11/tdocs-mapping.JPG"><img style="width: 400px; height: 400px;"  src="http://picupper.com/2009/06/11/tdocs-mapping.JPG"></a>
</p>

<p>
<a  href="http://picupper.com/2009/06/11/tdocs-tables.JPG"><img  style="width: 400px; height: 400px;" src="http://picupper.com/2009/06/11/tdocs-tables.JPG"></a>
</p>

A central user-to-pool mapping database, which is shared by three web apps: (a) all the TiddlyDocs' servers, specifically their Challenger module; (b) an admin app for managing the mappings (typical Django/Rails app with forms generated from data model); (c) a user-facing app (possibly a gadget in our envisioned OpenSocial scenario) showing the user (already authenticated via single-sign-on) a dropdown of instances they can launch.