---
id: 574
title: 'TiddlyDocs User Authentication &#8211; Generic Design and Custom Features'
date: 2009-08-14T18:38:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=574
permalink: /tiddlydocs-user-authentication-generic-design-and-custom-features/
dsq_thread_id:
  - "389128240"
categories:
  - SoftwareDev
tags:
  - Osmosoft
  - Security
  - TiddlyDocs
  - tiddlyweb
---
We are working on a design that will keep TiddlyDocs as generic as possible. The core TiddlyDocs product will have a concept of "rooms". This is the same kind of room you see in online forums or chat sites, where everyone inside the room contributes and sees content inside the room they're in, and can't see or do anything about rooms they're not in.

Our design works like this. Each room is a recipe of several room-specific bags, along with a global config bag. Each room is associated with a unique user role.

<img style="width:400px;" src="http://yuml.me/diagram/scruffy/class/%5BUser%5D*-*%5BRole%5D%2C%20%5BRole%5D-%5BRoom%20recipe%5D%2C%20%5BRoom%20recipe%5D+--%3E%5BGlobal%20Config%20bag%5D%2C%20%5BRoom%20recipe%5D++1-%3E%5BRoom%20Config%20bag%5D%2C%20%5BRoom%20recipe%5D++1-%3E%5BRoom%20Content%20bag%5D%2C%20%5BRoom%20recipe%5D++1-%3E%5BRoom%20Comments%20bag%5D" />

Note the role is used inside the respective bags' policy files, and they each vary somewhat. e.g. the comments bag says readable by everyone in 'role', appendable ("create tiddler" permission) by everyone in 'role', editable by "#(role)_admin". (ie there is a second role called "role_admin".); whereas the content bags says readable and writeable and editable by everyone in 'role'; and the config bag says readable by everyone in 'role', appendable by '#{role}_admin".

For now, there's a "makeroom" script that generates the recipe, the bags and the policies. (I'd ideally like to see the recipe be "magic" in some respects, using a wildcard mechanism).

That's the basic design. We also have some unique challenges in this particular installation - (a) users are authenticated using a custom, enterprise-specific, single-sign on solution, where the incoming header for each request identifies user's ID and (effectively) company; (b) we have certain rooms whose composition is manually configured and are a subset of the company's membership, and we also have a "everyone" room which is automatically composed of everyone in the company (e.g. we might have a "megacorp-everyone" room along with the manually configured "megacorp-accounting" room, and "megacorp-marketing" room); (c) to let users allocate specific TiddlyDocs to users, we need a dropdown containing real names of all users.

<img style="width: 400px;" src="http://picupper.com/2009/08/17/tiddlydocsrooms.png" />

BTW I'm simplifying some of the finer details here to make the discussion more pertinent to the general topic of TiddlyWeb/TiddlyDocs, rather than our specific problem. All of the following will be developed as proprietary plugins for our own installation. It's a somewhat complicated set of requirements because it's a real-world enterprise problem, where we have specialised requirements, combined with integration issues where we can control some things, but can't control others. (e.g. We can't change the underlying user store, where we would ideally store which rooms a user is in, instead of holding secondary user records inside TiddlyDocs.)

We will be building a TiddlyWeb plugin that sets the "extractor" filter. This is one of the several filters the request is subject to, on the way into TiddlyWeb. It is usually paired with the challenger filter - where challenger might present a username/password form and set a cookie, and extractor will read the cookie and set usersign (aka user ID) and any other info like users' roles. In this case, though, we already have the header set, so we don't need a challenger at all. We simply need an extractor that sets the usersign from the incoming header, and also notes the user's company. Verification will then check that (a) if the user is attempting to access the "everyone" company room, they are a member of the company; (b) if the user is attempting to access a "manual" company room, they are a member of the company *and* they have the role associated with the company. We use a naming convention to determine which company  a manual room belongs to.

On (c), we need a tiddler in the room "config" bag containing a list of user names. So in addition to the custom extractor, we will also need a periodic script to poll the user store associated with the SSO system. This will give us all the info about users in each company, so we can build up a mapping from company to list of users, where each user record has an ID and name. company-&gt;list[{user ID, user name]}. The script will then (a) rewrite the list of user names for the "everyone room" based on the company list, by effectively "copying" the results for that company (b) rewrite the list of user names for each manual room, by walking through each user, checking their roles, and accumulating their user name into the room list for each room they're in (c) do some cleanup - removing TiddlyWeb records for any users not in the list.

There's nothing very elegant about these custom implementations, and I've primarily written these details for the benefit of myself and colleagues who are implementing these custom features. The more interesting, general, point here is about <a href="http://jaybyjayfresh.com/2009/04/24/motivation-and-common-ground/">open-source and plugins</a>. TiddlyWeb's architecture allows us deliver a generic solution for TiddlyDocs rooms, which is applicable to any organisation, and we can then superimpose a custom feature  using the plugin mechanism. Furthermore, the plugin mechanism is a great way to decouple concerns - plugins are moduels on steroids. The core TiddlyDocs developer can concentrate on building an open-source, functional, multi-room TiddlyDocs edition, using the default authentication mechanism. Meanwhile, other developers can work in parallel on custom plugins.

(This post is a refinement of <a href="http://softwareas.com/tiddlydocs-tiddlycms-and-permissioning-models">this post</a>; we have been doing further thinking as we get closer to the final product and we learn more about our external environment.)
