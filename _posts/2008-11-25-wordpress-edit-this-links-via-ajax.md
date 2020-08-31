---
id: 496
title: 'WordPress &#8220;Edit This&#8221; Links via Ajax'
date: 2008-11-25T18:13:19+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=493
permalink: /wordpress-edit-this-links-via-ajax/
dsq_thread_id:
  - "375574002"
categories:
  - SoftwareDev
tags:
  - Ajax
  - AjaxPatterns
  - Javascript
  - Wordpress
---
Working on a WordPress customisation recently, I added an "Edit This" link which only logged-in people can see. To get caching right, the server always outputs the same thing - an invisible link - and only in the browser does the decision get made to show the link or not. This exemplifies the pattern I only ever identified as <a href="http://softwareas.com/ajax-as-a-remedy-for-the-cacheability-personalization-dilemma">"Ajax as a Remedy for the Cacheability-Personalization Dilemma"</a>, but which I will now call "Browser-Side Personalisation".

In this case, the personalised content is not secret, so it's fine to output it in the HTML, and simply make it invisible by default. And it's not mission-critical either, so the app degrades nicely if Javascript isn't present - it simply won't be displayed and the user will have to go into the "Manage Posts" area and look up the post from there.

To output "Edit This" from the server, within a WordPress loop:
[javascript]
  <div class="editPostLink"><? edit_post_link() ?></div>
[/javascript]

Links of this nature are rendered invisible within layout.css:
[css]
.editPostLink { display: none; }
[/css]

... but we switch them on if the user is logged in:
[javascript]
  var loggedIn = /wordpress_logged_in/.test(document.cookie);
  if (loggedIn) $(".editPostLink").show(); // it's easy with JQuery
[/javascript]