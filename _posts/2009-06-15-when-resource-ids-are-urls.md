---
id: 547
title: When Resource IDs are URLs
date: 2009-06-15T13:57:29+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=544
permalink: /when-resource-ids-are-urls/
dsq_thread_id:
  - "375574251"
categories:
  - SoftwareDev
tags:
  - Javascript
  - Osmosoft
  - REST
  - Scrumptious
  - tiddlyweb
---
Being a web app about websites and other resources, Scrumptious has a resource which is basically a URL, called "Pages". A Scrumptious resource modelling google.com/about looks like:

http://scrumptious.tv/comments/bags/ pages/tiddlers/http%3A%2F%2Fgoogle.com%2Fabout

See? The resource ID is http://google.com/about, encoded. (<tt>encodeURIComponent("http://google.com/about"</tt>)

This was working fine on my dev machine, running "twanager server comments.boz 8080" (comments.boz being an alias for my local machine). But on the server, and run through apache and TiddlyWeb's apache.py, it failed:

<a href="http://img.skitch.com/20090615-jsr1e1bxupi8w9cdrbjspc6fkd.jpg"><img src="http://img.skitch.com/20090615-jsr1e1bxupi8w9cdrbjspc6fkd.jpg" style="width: 400px;"></a>

The fix was twofold - both of the following were required:

<ul>
  <li><tt>AllowEncodedSlashes On</tt> in apache config. This option ensures encoded slashes (%2F) are passed through to the end-app.</li>
  <li><a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers/pathinfohack">PathInfoHack plugin</a> As with any TiddlyWeb plugin, I downloaded it and added it to 'system_plugins' list in tiddlywebconfig.py. (Thanks <a href="http://cdent.tumblr.com/">Chris</a> for the pointer.)</li>
</ul>

And now we can happily talk resources with URLs as IDs to the server.

<a href="http://img.skitch.com/20090615-r5ahedxfg61m2ybc8iag9be581.jpg"><img src="http://img.skitch.com/20090615-r5ahedxfg61m2ybc8iag9be581.jpg" style="width: 400px;" /></a>