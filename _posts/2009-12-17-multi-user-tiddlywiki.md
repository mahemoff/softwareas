---
id: 744
title: Multi-User TiddlyWiki
date: 2009-12-17T01:25:38+00:00
author: admin
layout: post
guid: http://softwareas.com/multi-user-tiddlywiki
permalink: /multi-user-tiddlywiki/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574574"
categories:
  - SoftwareDev
tags:
  - Osmosoft
  - TiddlyDocs
  - tiddlyweb
  - TiddlyWiki
  - TiddlyWiki MU
---
<a href="http://www.kenrockwell.com/nikon/d300/color.htm"><img style="width: 400px;" src="http://www.kenrockwell.com/nikon/d300/images/saturation/300_0719-flowers.jpg" /></a>

TiddlyWiki MU is what I'm calling - in the absence of an official name - an effort within Osmosoft to pull together a bunch of work into something that will be very useful in the enterprise and beyond. You could also call it "tiddlywiki as a service" or "multi-room tiddlywiki". Similar to Wikia or WordPress MU, you can spin off a new multi-user instance with a "single click". This is "MU" in the sense that there's already a TiddlyWeb-backed TiddlyWiki product (TiddlyWebWiki). The value-add of TiddlyWiki MU (or whatever it ends up being called) is that you can make a new instance of such a thing without being a system administrator and without going through the effort of building it on the server. This is exactly like the way WordPress MU lets you spin off a new blog without having to set up a new instance of WordPress on the server.

In addition to the ease of spinning off new instances, there's an important side benefit from this architectural pattern: synergy. From a user's perspective, they only have one URL to remember/bookmark/share/link; once at that URL, the system can helpfully guide them through the different instances they have access to. Also, it would be possible to make content that's used across different rooms. For example, give each user a private bag of tiddlers and they could use it to set their global preferences (with the right UI).

The whole thing is an open-source server, so an enterprise can just download it, deploy it, and let a thousand flowers bloom as users spin off new instances and do what they will. The really important thing here is that<strong> tiddlywiki is not just a wiki, but a framework for web apps</strong>. Room admins can easily perform customisations like changing the stylesheet; or go so far as coding up Javascript plugins to radically alter look-and-feel. More importantly, they can update the room's recipe to include a bags of tiddlers sitting elsewhere on the system. That bag might be the <a href="http://tiddlydocs.com">TiddlyDocs</a> system for instance, if they are interested in collaborative document publication, or it might be <a href="http://tiddlyguv.com">TiddlyGuv</a> if they want an open-source governance system. They can then fine-tune those systems according to their own needs.

Here is a rich user story (a rich user story is like a regular user story, but it deliberately includes detail that a "pure agile" developer might object to as "getting ahead of yourself" , You-Ain't-Gonna-Need-It, or unverifiable; while those objections are valid reasons not to use the story as a direct input to coding or task breakdown, and while rich visions are inevitably too premature to turn out into accurate forecasts, they do help to prove you're heading in the right direction, to motivate user-centric developers like myself, and to illustrate what you're doing to people outside the project) ...

(cue dream sequence)

<a href="http://www.michellepike.com/Gallery2.html"><img src="http://picupper.com/2009/12/16/Dream_Sequence_II_op_394x600.jpg" style="width: 250px;"></a>

----

<em>Jimmy is a moderately experienced TiddlyWiki user and wants to make a room for the enterprise's music club to collaborate on compositions. So he logs into TiddlyWiki MU, hits "New Room", and creates a room called "musicians". He then sees the new room - a vanilla TiddlyWiki with a list of users down the side: currently, just Jimmy, with an Admin icon beside his name. He ignores the "Invite Users" button for now so he can concentrate on setting up the room.
<em>
The groups wants to put out compositions as collective anthologies, so he decides TiddlyDocs will form the basis of this room. Thus, he clicks on "Manage Room" and a lightbox appears. It shows him the technical detail of the room on one side of the dialog - the bags that make up the room's recipe. And on the other side, he can search and browse for new bags. He navigates to "tiddlydocs"  bag and hits the "Add" button beside it. It now appears on the top of the room recipe.

<em>Dismissing the lightbox and reloading, the "musicians" room is now a vanilla TiddlyDocs. He clicks on the backstage button on the top of the page and edits a few tiddlers - SiteTitle, SiteSubTitle, and ColorPalette, to give the room its own identity. He also needs a way for the participants to enter musical compositions. Luckily, he already has a standalone TiddlyWiki for music composition, with a Music plugin in it. From backstage, he pulls up the Import dialog and uploads the Music plugin from there. For each imported tiddler, there's a dropdown showing the bags he can import it into ("musicians-config", "musicians-comments' etc). He indicates it should go in the musicians-config bag. On reloading the page, he finds something is broken - he can't add musical notes from the TiddlyDocs editor. It's time to call a friend ...

<em>He clicks "Invite Users" and up pops a modal dialog where he enters the email address of Dwight Doomore, a TiddlyWiki expert he's fortunate to know. He checks the "make this user an admin" box and in the optional message area, explains the problem he's having. Dwight clicks on a link in the subsequent email and he's up and running inside the slightly broken "musicians" room. Donning his cyber-shades with Matrix-like precision, he proceeds to create a new plugin tiddler and monkey patches the Music plugin functionality so it plays nicely with TiddlyDocs. Then he tests it by writing up the first new composition, pulls up the user admin panel to remove himself from the room, and replies to Jimmy that it's all taken care of.</em>

<em>Pleased with the result, Jimmy writes a few compositions, re-arranges them using TiddlyDocs' tree control, and adds a little text. Instead of using "Invite Users", he just mails his colleagues the URL of the "musicians" room. They each visit the URL, indicate they wish to join, and a few days later, Jimmy jumps into the user admin panel, where he can accept their requests to join. Now they can all work together on different documents within the one room, and TiddlyDocs provides enough functionality to control how the final copies will be published.

<em>Six months later, the first "enterprisey musicians" composition book is printed and bound.</em>

-----

A single TiddlyWiki MU server has the capacity to facilitate a thousand stories like this, each of them with its own unique characters and quirks. There are plugins for voting, blogging, commenting, structured writing, quizzes, graphics, social bookmarking ... it will be fun to see how users deal with all that. Most likely, it will follow the usual pyramid structure:

* Many users will just create a vanilla room - plain old (multi-user) tiddlywiki. Of these, some will just make it a private scratchpad for themselves and never invite anyone at all.
* Some users will make the room become a vanilla edition of a specialised application for their group to work on. e.g. collaborate on publication-ready docs with TiddlyDocs; collect and annotate websites with Scrumptious; brainstorm and vote on innovations with New Ideas.
* A smaller number of users will customise the config tiddlers; pull in extra plugins; build new room-specific plugins; or attempt to combine multiple bags.
* An even smaller number of users will have to deploy a standalone customised server, perhaps deploying a customised edition of TiddlyWiki MU with certain server-side plugins and configurations. This is the kind of thing you might do if using TiddlyWiki MU for a hardcore, full-fledged, 110% uptime, supported to the teeth, enterprise web app. You'd perhaps run a pilot on the regular TiddlyWiki MU server and then perform a (relatively effortless) migration onto its own dedicated server. Or a power user might just hand-configure a TiddlyWeb instance from parts. (This is where we get into "TiddlyWeb as a generic RESTful server" territory.)

The first case is already well-supported by other wiki platforms, so it's nice and all being open-source and TiddlyWiki-based, but not really the killer app. The second is really the sweet spot when it comes to optimising user experience in the short term. We've spent a lot of time at Osmosoft thinking about how to deploy "TiddlyDocs" as a standalone package. That's still interesting, but I think it's a lot more interesting to ask how to deploy TiddlyWiki MU as a standalone package, and then let users go into web app and make a new "TiddlyDocs" instance with one click. The third case is supported by the general TiddlyWeb model and doesn't need any special optimisation at this stage.

<em>[There's a <a href="http://groups.google.com/group/tiddlyweb/browse_thread/thread/ff79c6a5cd4c70b1">thread about some of this stuff</a> on the mailing list, so I've switched off comments to keep the conversation in one place.]</em>