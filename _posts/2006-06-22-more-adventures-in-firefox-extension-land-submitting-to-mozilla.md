---
id: 311
title: 'More Adventures in Firefox Extension Land: Submitting to Mozilla'
date: 2006-06-22T01:26:27+00:00
author: admin
layout: post
guid: http://www.softwareas.com/more-adventures-in-firefox-extension-land-submitting-to-mozilla
permalink: /more-adventures-in-firefox-extension-land-submitting-to-mozilla/
dsq_thread_id:
  - "375572983"
categories:
  - SoftwareDev
tags:
  - AddOn
  - Extension
  - Firefox
  - Greasemonkey
  - Links
  - Mozilla
  - Plugin
  - Teleporter
---
I recently explained how I <a href="http://www.softwareas.com/domain-teleporter-greasemonkey-script">created my first Greasemonkey script</a> as an experiment, then <a href="http://www.softwareas.com/teleporter-from-greasemonkey-to-self-contained-extension">converted it</a> to a standalone Firefox plugin/extension/add-on using an automated tool. <a href="http://mahemoff.com/project/teleporter/">Official homepage here</a>. <b>The experiment continues, as I subsequently submitted it to Mozilla, and it's now been approved as an official plugin.</b>

I've been curious about the process people go through to submit an official extension, so here's the rundown.

<h3>1. Upload XPI File</h3>

Standard upload of the XPI file, which contains all the plugin contents.

<h3>2. Provide Metadata</h3>

... such as my name, the extension's homepage, and so on. (Why isn't this info just packaged inside the XPI file? Actually, some of it is already in that file anyway.)

<img src="http://img109.imageshack.us/img109/6059/addextension6si.png" width="500" height="450"/>

One interesting thing here is that I get to choose the category it goes in (although I guess the approver could change it later on). Note also that there's no help about the categories on this page, so I think there's a large risk that developers will probably be inconsistent. Not bashing Moz about this, but I do think they could make it easier for end-users to locate plugins if they encouraged consistent labelling - I've sometimes trawled through 5 or 6 pages trying to find a plugin within a particular category.

<h3>3. Wait for Approval</h3>

<img src="http://img465.imageshack.us/img465/8984/addextension29wn.png" width="500" height="200"/>

An official Mozilla person must now look it over, which is a reassuring security measure. (Complain all you want about Ajax and its tabloidistically alleged "security holes", but the open-source nature of web architecture is extremely compelling from a security perspective.)

After about thirty hours, I received an email that the plugin had been approved. <a href="https://addons.mozilla.org/firefox/2816/">And now it's available from Mozilla</a>, ID 2816.

<img src="http://img213.imageshack.us/img213/4441/addon7id.png"/ width="500" height="200">

If you told me I was cluttering up the space of extensions with this trivial 7KB contribution, I'd say you're probably right, but then what's the harm in lots of extensions, as long as it's easy to locate the one you want. (<a href="http://userscripts.org">UserScripts.org</a>, the GM repo, does that to great effect with the power of tagging, and a wiki would make it even more useful.) Not everyone wants to set up GM and maintain the scripts, even those who are savvy enough to know about extensions.

<b>In summary, Greasemonkey and associated tools make it easy, bordering on trivial, for anyone with basic Ajax knowledge to create a standalone Firefox extension</b>. Of course, it will be functionally limited to GM-type page munging, but it's still a lot easier than I had imagined.
