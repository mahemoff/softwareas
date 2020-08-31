---
id: 324
title: Ajax as a Remedy for the Cacheability-Personalization Dilemma
date: 2006-07-13T11:37:10+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-as-a-remedy-for-the-cacheability-personalization-dilemma
permalink: /ajax-as-a-remedy-for-the-cacheability-personalization-dilemma/
dsq_thread_id:
  - "375573015"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Caching
  - Cookies
  - Customisation
  - Customization
  - Javascript
  - Links
  - Personalisation
  - Personalization
  - REST
  - RESTful
  - Session
  - XMLHttpRequest
---
A pattern for your consideration, about using Ajax to help pages be RESTful. 

<h3>Problem</h3>

How to personalize content and make pages cacheable and bookmarkable at the same time?

<h3>Forces</h3>

<ul>
<li>We want pages to have clean URLs that describe the main content being viewed. Doing so makes pages easily bookmarkable and send-to-friend-able, and also allows us to cache the page anywhere along the way. For example, viewing info about Fight Club should be  <i>http://example.com/fightclub</i> and not <i>http://example.com/fightclub/user-mahemoff</i> or <i>http://example.com/fightclub/287490270-1931321-cijE12ZSz</li>.
<li>We want to personalize pages - say Hi to the user, show them personalized recommendations, etc.</li>
<li>If we personalize, but use the same URL for all users, we break REST and therefore won't be able to cache any content. My http://example.com/fightclub is different to your http://example.com/fightclub because we each see our own recommendations inside the page. 
<li>But if we use diferent URLs for personalization, we can't cache across users and pages aren't sent-to-friend-able. If I look up and see http://example.com/fightclub/user-mahemoff, I'm probably not going to bother sending you the URL. Furthermore, my view of the page can't be cached.
</ul>

<h3>Solution</h3>

<b>Create pages generically (same version for all users), and in this generic version, embed a remoting call which will customize the page for the current user.</b> Serve http://example.com/fightclub to everyone. Then everyone's browser makes a further call to grab custom content (Multi-Stage Download). This additional call is unRESTful as the server will use cookies to decide what content to return, but at least we've isolated that component, served the bulk of the content without caching, and given the user something they can bookmark and send to their friends.

<h3>References</h3>

<ul>
<li><a href="http://groups.yahoo.com/group/rest-discuss/message/5997">Post by Bill Venners</a></li>
<li><a href="http://www.artweb-design.de/articles/2006/04/28/thinking-about-restful-dynamic-web-applications">@rtweb Design: Thinking about RESTful dynamic web applications</a></li>
<li><a href="http://ajaxpatterns.org/RESTful_Service">RESTful Service @ AjaxPatterns</a> Note that it's about Services, whereas this pattern sketch is about RESTfulness of the actual page.</li>
</ul>