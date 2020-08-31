---
id: 531
title: TiddlyGuv
date: 2009-04-11T15:39:08+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=528
permalink: /tiddlyguv/
dsq_thread_id:
  - "375574191"
categories:
  - SoftwareDev
tags:
  - Ajax
  - FOSSBazaar
  - Governance
  - Javascript
  - open source
  - Osmosoft
  - TiddlyGuv
  - tiddlyweb
  - TiddlyWiki
---
I've just presented TiddlyGuv at the FOSSBazaar workshop, the event I <a href="http://softwareas.com/fossbazaar-workshop">wrote about</a> yesterday. It's a good time to introduce TiddlyGuv - I've mentioned it in some talks and tweeted about it on occasion, but this is its maiden appearance on Software As She's Developed.

<a href="http://www.tiddlyguv.org">TiddlyGuv</a> (that's a code name we'll use for a while) is a web app to support open source software governance. In promoting and supporting open source at Osmosoft, one of the activities is a governance process. This means establishing policies for open source usage and auditing projects against it. TiddlyGuv is the tool we're developing to support this process - it will support community discussions, policy publication, project tracking, workflow, and alerts about potential problems.

A few things about TiddlyGuv:

<ul>
<li> TiddlyGuv is in progress, it's not complete and still needs work around a clean installation package. (We're currently re-working how all this is done with TiddlyWeb verticals; once that's done, there will be a package so people can try it out.) In any event, the code in some form is <a href="http://trac.tiddlywiki.org/browser/Trunk/contributors/MichaelMahemoff">online in Trac</a>.</li>
<li>TiddlyGuv is a web app. No surprise there :).</li>
<li> TiddlyGuv motivated the <a href="http://tiddlywiki.mahemoff.com/CommentsPlugin.html">comments plugin</a>, which has now been used in various other projects, including the live <a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers.wiki">TiddlyWeb documentation wiki</a>.</li>
<li> TiddlyGuv is built on the TiddlyWiki-TiddlyWeb stack, like <a href="http://tiddlydocs.com">TiddlyDocs</a>. We see a general trend of CMS apps emerging on this stack, which has been called TiddlyCMS. (TiddlyCMS is an architectural pattern.) The aim is that TiddlyCMS apps share a large suite of common components such as the comments plugin.</li>
<li> TiddlyGuv is open source. The license hasn't been finalised, but will likely be BSD, same as TiddlyWiki. We hope other organisations use TiddlyGuv in ther own organisations; TiddlyWiki and TiddlyWeb offer highly flexible architectures which lend themselves to adaptability.</li>
</ul>

Functionally, the first thing we're aiming for is a tool with document wiki, for general discussion about open source usage, and a license portal, showing a list of licenses and information about each one. The comments plugin ensures each document and each license can be commented on too. All of this is there today, albeit in an untested state. Later on, we will add info about projects and further still, a workflow tool - for example, "Once the project form has been submitted, it must be reviewed by two named reviewers. They will each receive an email notification when a project is ready for review." We would want the system to follow rules like that, and we would want to allow site administrators to maintain such rules. The TiddlyWiki model is to encapsulate rules like that inside tiddlers. I foresee some kind of Javascript-powered <a href="http://ajaxian.com/archives/metaprogramming-dsl-javascript-presentation ">Domain-Specific Language (DSL)</a>.

The FOSSBazaar slide pack:

<div style="width:425px;text-align:left" id="__ss_1272956"><a style="font:14px Helvetica,Arial,Sans-serif;display:block;margin:12px 0 3px 0;text-decoration:underline;" href="http://www.slideshare.net/mahemoff/fossbazaar-tiddlyguv-demo?type=presentation" title="FossBazaar TiddlyGuv Demo">FossBazaar TiddlyGuv Demo</a><object style="margin:0px" width="425" height="355"><param name="movie" value="http://static.slidesharecdn.com/swf/ssplayer2.swf?doc=foss-tiddlyguv-090410120907-phpapp01&stripped_title=fossbazaar-tiddlyguv-demo" /><param name="allowFullScreen" value="true"/><param name="allowScriptAccess" value="always"/><embed src="http://static.slidesharecdn.com/swf/ssplayer2.swf?doc=foss-tiddlyguv-090410120907-phpapp01&stripped_title=fossbazaar-tiddlyguv-demo" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="355"></embed></object><div style="font-size:11px;font-family:tahoma,arial;height:26px;padding-top:2px;">View more <a style="text-decoration:underline;" href="http://www.slideshare.net/">presentations</a> from <a style="text-decoration:underline;" href="http://www.slideshare.net/mahemoff">mahemoff</a>.</div></div>

The feedback from the workshop was positive; there's interest in the project and there was also interest from one vendor of a commercial product about ways to introduce the wiki or commenting aspects into an existing product. A good example of this sort of thing is Amazon - the way it has a structured product page, which incorporates a forum and a wiki. It raises some interesting architectural issues about how a TiddlyWiki/TiddlyWeb  app could be embedded onto a page as a widget-style component, with identity and permissioning handled too. I also had an extended discussion with Mark Donohoe about how TiddlyGuv could talk to <a href="http://www.fossology.org/">FOSSology</a>. Of which, more in the next post.