---
id: 549
title: 'Scrumptious Update: Open ID Support, UI Enhancements'
date: 2009-06-17T17:45:10+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=546
permalink: /scrumptious-update-open-id-support-ui-enhancements/
dsq_thread_id:
  - "386793615"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Comments
  - Javascript
  - Osmosoft
  - REST
  - Scrumptious
  - tiddlyweb
---
I've released a new version of <a href="http://scrumptious.tv">Scrumptious</a>. Main change is it now supports Open ID. You can click a "login" link to comment by Open ID. It's optional by default, though a Scrumptious site operator could easily make it mandatory for read, write, or both by just changing a couple of words in the "policy" config files. Similar to other CMSs like WordPress, non logged in users can indicate their name and URL when they submit a comment.

There are also UI enhancements - the design is cleaner and looks closer to the original <a href="http://tiddlywiki.mahemoff.com/CommentsPlugin.html">original TiddlyWiki comments plugin</a>. Interestingly, I retained almost identical markup, so I was able to cut-and-paste the original CSS for the comments plugin and it mostly worked. I also now include the default TiddlyWiki stylesheets as well. It's not just look-and-feel which is closer to the original plugin, but the content - you now have info like modifier, modified date, and a permalink available.

I also added something I always wanted to add on the original plugin, which is some animation, e.g. when you add a new reply, the page scrolls to that reply, and a yellow fade effect highlights it. This is a genuinely useful feature as I was finding it difficult to see which reply I'd just added, when there are a lot of comments around.

<a href="http://img.skitch.com/20090617-b7x62uf2x6qs2873h9rsmrap7u.jpg"><img style="width: 400px;" src="http://img.skitch.com/20090617-b7x62uf2x6qs2873h9rsmrap7u.jpg"></a>

I've also begun work on a <a href="http://scrumptious.softwareas.com/comments/static/commentsReport.html">Comments Report</a> showing recent comments. Obvious related enhancement is to take the TiddlyWeb Atom plugin and make a comments feed.

Right now, all this is only tested on Firefox (the original was tested on all browsers, at least the full website view); my next priority is to work on browser compatibility, and after that, extract a modular JQuery comments plugin.

<h3>Implementation Notes</h3>

Regarding the implementation, TiddlyWeb ships with Open ID by default (Open ID is one of two default challengers, the other being the usual simple user-pass key pair config). The most challenging thing here was getting the UI right for both anonymous users and logged in users, as well as handling a redirect in the popup after a successful login; but at the back end, Open ID "just works".

In summary, I added Open ID support as follows:
<ul>
  <li>Add a "login" link to the TiddlyWeb OpenID challenger UI, using a "target" attribute so the challenger opens in a popup.</li>
  <li>The challenger URL in that link also contains a redirect param, which I redirected to a new static page. This static page shows the user their login ID (by inspecting the "tiddlyweb_user" cookie value), calls a callback "onLogin" method on the original page, and closes itself.</li>
  <li>The "onLogin" callback updates the login display to show the logged in user and a logout link; the logout link simply runs some Javascript to remove the cookie. The callback also updates any forms that are open prompting for bio info; it hides this info and in its place, shows the current user ID (read-only).</li>
</ul>

Thanks to <a href="bengillies.net/ ">Ben</a> and <a href="http://cdent.tumblr.com/">Chris</a> for pointing me in the right direction on TiddlyWeb's Open ID support.

PS I discovered late in the day (literally) that TiddlyWeb lets the client specify whatever modifier they want