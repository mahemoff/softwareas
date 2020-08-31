---
id: 418
title: 'Widget/Gadget Containers: What are they good for?'
date: 2008-02-04T17:59:45+00:00
author: admin
layout: post
guid: http://www.softwareas.com/widget-containers-what-are-they-good-for
permalink: /widget-containers-what-are-they-good-for/
dsq_thread_id:
  - "375352441"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Gadgets
  - Links
  - OpenSocial
  - Web
  - Web 2.0
  - Widgets
---
<tags>Ajax, AjaxPatterns, Gadgets, OpenSocial, Shindig, Web, Web 2.0, Widgets</tags>

<a href="http://www.google.com/ig"><img style="width:350px; height: 220px;" src="http://img210.imageshack.us/img210/1558/igooglebr3.png" /></a>

<h3>Background</h3>

Widgets are small "mini websites", typically self-contained blocks of content, on a larger web page (with Ajax Design Patterns, I referred to them by the nom du jour <a href="http://ajaxpatterns.org/Portlet">Portlets</a>). They are used in a couple of ways:
<ul>
  <li><strong>Embedded in a normal web page.</strong> For example, my blog currently contains a BBC weather widget and a "Twitter Badge" showing my latest tweets. Widgets embedded in this way are combined by the publisher, often with some manual HTML coding (script tags), and are usually a sideshow affair.</li>
  <li><strong>Combined within a widget container (aka "widget portal", "Ajax homepage").</strong> Websites such as <a href="http://www.google.com/ig">iGoogle</a> and <a href="http://netvibes.com">NetVibes</a> are primarily designed as widget aggregators, allowing an end-user to construct a personalised page for themselves. They are the Ajax/Web 2.0 successors of the "My &lt;whatever&gt;" hype (My Yahoo!, My Excite!, etc.) of the mid-to-late '90s. To some extent, a social networks like Facebook fits into this category too, with the proliferation of applications available to users to embed on their homepages. And as Facebook in particular illustrates, widget containers are not always private "productivity tools", but may also be available to a user's friends or the general public. Indeed, the more conventional widget containers have recently started allowing users to make their <a href="http://www.pageflakes.com/fitness">public portals</a>, which starts to move them in the territories of CMS and social networking.</li>
</ul>

Well, this is an article is about widget containers. Specifically, I'm currently compiling a list of typical features you'd expect to see in widget containers, so if this post sounds stream-of-consciousness, well, it sort of is.

<h3>Anatomy of a Widget (well, Gadget and OpenSocial) Container</h3>

A good place to start is the breakdown of functionality for Shindig, the new Google-supported Apache project to build a reference implementation for the OpenSocial standard. OpenSocial is heavily intertwined with the whole idea of widgets and widget containers, since it's basically Google Gadgets + standardised social networking APIs. Hence, Shindig is essentially <em>the</em> high-profile open-source project involving a widget container. <a href="http://opensocialapis.blogspot.com/2007/12/lets-get-this-shindig-started.html">Shindig has been broken into four parts</a>:
<blockquote>
<ul>
<li> Gadget Container JavaScript -- core JavaScript foundation for general gadget functionality (read more about gadget functionality). This JavaScript manages security, communication, UI layout, and feature extensions, such as the OpenSocial API.
<li> Gadget Server -- an open source version of gmodules.com, which is used to render the gadget xml into JavaScript and HTML for the container to expose via the container JavaScript.
<li> OpenSocial Container JavaScript -- JavaScript environment that sits on top of the Gadget Container JS and provides OpenSocial specific functionality (profiles, friends, activities).
<li> OpenSocial Gateway Server -- an open source implementation of the server interface to container-specific information, including the OpenSocial REST APIs, with clear extension points so others can connect it to their own backends.
</ul>
</blockquote>

That's a very useful overview, though I'm looking more at specific features which generally cut across at least some of these parts. For example, gadget preferences. These are part of the container Javascript because there is a UI to change the preferences, they are part of the gadget server because it must initialise the gadget according to preferences, and they are part of the server because they must be persisted.

<h3>Feature List</h3>

First cut at a feature list (# indicates not directly available in iGoogle)

<h4>Gadget Preferences</h4>

* Preference defaults
* User can set preferences
* Publisher can set preferences when embedding widget on a page
* Preference variable types: string, enumerable (set by dropdown, set by combobox), boolean, list, location, etc
* Preference persistence: by database against session vs. in cookie
* Preferences persisted for anonymous user (<a href="http://ajaxpatterns.org/Lazy_Registration">Lazy Registration</a>)
* Gadgets can access preferences via API, consistent access regardless of content type and embedding model
* # Gadget can be notified of preference changes, so that it's not necessary to reload the entire gadget/page after each change

<h4>Gadget Appearance</h4>

* Gadget appearance customisable by publisher
* Gadget appearance customisable by user
* # Round corners, shadows, background images (e.g. <a href="http://wayne-sutton.com/blog/wp-content/uploads/2007/03/schmedley.jpg">Schmedley</a> has all of these)

<h4>Gadget Content Type</h4>

See <a href="http://www.softwareas.com/where-do-widgets-come-from-a-look-at-widgetgadget-content-types">Widget Content Type article</a>
* HTML - from container provider's domain
* URL - from gadget provider's own domain
* # Inlined - embedded on container. This implies a security model, e.g. Caja

<h4>Container Appearance</h4>

* User can change gadget skin, header, footer, background, widget preferences via constrained mechanism (ie can't change everything; e.g. config file or UI)
* Publisher can change look and feel via HTML/CSS
* Gadget themes available, with gallery, for pre-defined configurations
* Animation used for features such as preference setting and expand/collapse of widgets
* Drag-and-drop shows preview of page appearance after drop

<h4>Container Layout</h4>

* Multi-column (usually 3) vs. freestyle
* Gadgets can be dragged around the page, displacing other gadgets
* Tabs allow for multiple layouts
 * Tabs can be renamed
 * Gadgets can be dragged into tabs

<h4>Gadget Manipulation</h4>

* Gadgets can be added
 * by URL (with security warnings etc)
 * from Gallery (see Gallery below)
 * by cloning a gadget on user's page or someone else's public page or external page
* Gadgets can be removed
* Can limit singleton gadgets to one instance per container

<h4>Gadget Gallery</h4>

* Gadgets displayed and rendered with metadata embedded in gadget spec, e.g. thumbnail image, author, etc.
* Gadgets can be browsed by category, date added, etc.
* # Users can tag gadgets and gadgets can be browsed by tags; tag cloud; etc
* Users can rate gadgets
* # Users can recommend gadgets to their friends
* Users can comment on gadgets

<h4>Gadget-To-Gadget Communication</h4>

* Gadgets can communicate with each other (Google PubSub)

<h4>Gadget Size</h4>

* # Gadget content can be expanded and collapsed (<a href="http://www.bbc.co.uk/home/beta/">BBC Beta Homepage</a>)
* Gadgets can be dynamically resized

<h4>Content Sharing</h4>

* Container can be made public (what happens to personalised widgets?)
* Container can be shared with "friends" (how are friends decided)
* Users can invite/permit/disallow friends to use their container

<h4>Gadget Services</h4>

* Proxying service
* Caching service (extends proxying service)
* OpenSocial (or generic social networking) service
* # Advertising service - Gadgets can serve as ads with revenue model
* # Financial service - Gadgets can charge for services (subscription, one-off, etc.)

<h4>Admin Functions</h4>
* Admin function to tweak gadget/theme rankings, scrutinise/moderate/eliminate gadget/theme submissions, etc
* Admin function to view metrics, e.g. number of page views, popularity of gadgets, back-end service usage (e.g. proxying and OpenSocial calls)
* Admin function to manage users (provide support, ban, etc.)