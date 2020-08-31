---
id: 533
title: TiddlyCMS Plugins from TiddlyGuv
date: 2009-04-22T17:21:20+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=530
permalink: /tiddlycms-plugins-from-tiddlyguv/
dsq_thread_id:
  - "390058475"
categories:
  - SoftwareDev
---
TiddlyGuv has a few features which other "TiddlyCMS" apps could benefit from. If that's the case, we ought to extract them into separate plugins (though I'd be reluctant to do it prematurely, until we know there is some demand for it). The point of this post is to outline some of those generic features of TiddlyGuv which are, or could be, extracted into plugins. Developers interested in this functionality can then let me know and help me extract the components from the current code base, and mould them in a way that will be useful to others too.

<h4>Comments</h4>

<img src="http://img.skitch.com/20090422-fmq4sbic2j22rsksfanp5g96ni.jpg" />

This one already is a <a href="http://tiddlywiki.mahemoff.com/CommentsPlugin.html">plugin</a> used in several apps: nested comments.

<h4>Public/Protected/Private Model</h4>

For general document tiddlers, a user may mark them as private or public. In addition, admin users can mark them as protected. All of this is already provided by TiddlyWeb, as long as you create the right bags, i.e. a private bag for each user, a bag that admins can edit but others can only read, and a public bag. In TiddlyGuv, the private user bag is created upon login, if it doesn't already exist, using a server-side plugin.

Anyway, yes - all of this is already provided in the server by TiddlyWeb. The challenge here was to provide a UI for it. In the case of licenses, it's like a "promotion" moving it from private to public. You promote by clicking on a button. Further stages are foreseen (e.g. reviewed, accepted) when TidldyGuv becomes more workflow-oriented.

In the case of documents, it's more like a simple status - is it private, protected, or public. You choose the status with a dropdown, as shown below in edit and view modes, respectively. It's slightly different, and I could possibly harmonise the two styles of access.

Edit View:

<img src="http://img.skitch.com/20090422-ejdcimc3dryi9iqhbq3twgjnbs.jpg"/>

Read View:

<img src="http://img.skitch.com/20090422-ref92ptai858ryde7sjg72ttgm.jpg"/>

All of this could be encapsulated as a UI-side plugin, whch accepts as parameters the names of the protected and public bags.

<h4>Mediawiki-Style Sections</h4>

A common TiddlyWiki pattern is to aggregate tiddlers together in a new tiddler. This is easy to do with markup, using the tiddler macro:
[html]
<<tiddler intro>>
<<tiddler arguments>>
<<tiddler conclusion>>
[/html]

It's also easy to do programmatically:
[javascript]
  var sections = store.getTaggedTiddlers("section");
  sections = sortByPriority(sections);
  /* for each section ... */
     /* append HTML element containing section.text */
[/javascript]

TiddlyGuv manages licenses, and each license has a standard set of sections such as plain English explanation, usage policy, and official license text. This could be generalised into "a set of configurable sections for each type of aggregate tiddler". For example, an aggregate "cv" (resume) tiddler type would have sections like "education", "work history", "achievements".

TiddlyGuv does aggregation, but also extends the pattern to include edit links on each section, similar to what you see in MediaWiki instances like <a href="http://wikipedia.org">the big W</a> and the <a href="http://ajaxpatterns.org">slightly less big A</a>. You have an edit link next to each section.

Another feature, not shown here, is collapsing large bodies of text. If the text is over, say 1024 characters, it simply shows the first few words along with a word count and a toggle control to show and hide the entire text.

A further feature is the "policy" section. Only admins may set this section, and it is rendered with a warning to that effect. Again, this is generalisable; for some types of content, some of the content may be world-editable while others may only be edited by admins. This feature ties the sectioning aspect to the previously discussed aspect related to permissioning. Again, it could be encapsulated in a sectioning plugin.

<h4>GUIDs</h4>

Traditionally, tiddlers are identified by their title. e.g. you can programmatically grab a tiddler by saying <tt>var stylesheet = store.getTiddler("StyleSheet");</tt>. This is like having a database table whose primary key is a meaningful field, such as a name. There are many debates over this kind of key in database design, and most modern schema designs use a dedicated ID field instead. That's what we need with TiddlyCMS apps, for two reasons: (a) tiddlers link to each other (such as aggregate tiddlers mentioned earlier); things would therefore get complicated if a tiddler was renamed, and that name was the primary key; (b) we sometimes want two tiddlers whose title is the same thing. For instance, in a single TiddlyDocs instance, we envision a "soup" of shared tiddlers which can be pulled into a document; a TiddlyDocs document is really just a hierarchical orchestration of existing tiddlers. For instance, a common "Disclaimer" section might appear in all documents. The problem arises when the user wants a deviation of the disclaimer's contents; the title must appear the same, but the tiddler will be different. This is not possible when titles are used as primary keys; hence the need for a separate  ID.

This will be achieved using the <a href="http://softwareas.com/guid0-a-javascript-guid-generator">Guid0 library</a> I built earlier. A TiddlyWiki plugin will be built, incorporating Guid0, intercepting certain calls like the call to create a new tiddler. It will store the user-meaningful title as a custom tiddler field, and make the tiddler's title value become a newly-minted GUID. It will also intercept tiddler display mechanisms to show the custom tiddler field instead of the GUID, so that users will be none the wiser. I may also include a second "detailed title" field so that users can write a description of the tiddler, which won't be rendered, but would be used to help them distinguish two tiddlers of the same title - when the tiddlers appear in a dropdown, for instance.