---
id: 491
title: For Browser Extensions, Grease is the Word
date: 2008-10-20T14:32:16+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=488
permalink: /for-browser-extensions-grease-is-the-word/
dsq_thread_id:
  - "375573980"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Chrome
  - Extensions
  - Firefox
  - Greasemonkey
  - Javascript
---
<img src="http://www.nokilli.com/sacto/images/greasemonkey.jpeg" />

<a href="http://googlesystem.blogspot.com/2008/10/google-chrome-to-add-greasemonkey.html">Chrome now has Greasemonkey support</a>. The Chromium patch came from <a href="http://blog.youngpup.net/">Aaron Boodman</a>, who is at once a Google employee and the brains behind <a href="https://addons.mozilla.org/firefox/addon/748">the original Firefox Greasemonkey extension</a>.

It makes me wonder if this is the plan for Chrome add-ons. Forget about anything like Firefox's add-on mechanism and just rely on Greasemonkey. With the right APIs, it's all you need.

For a long time, I have been confused and disturbed by the disparity between Greasemonkey and Firefox extensions. Creating a Greasemonkey extension is dead simple for any Ajax developer; creating a bona fide Firefox extension is more complicated, and involves writing the kind of meta-descriptions and JARs that most Ajax folk avoid. (The kind of simplicity mantra that has made JQuery king of the hill for now.)

You might recall I <a href="http://softwareas.com/tag/greasemonkey">automagically ported the domain teleporter Greasemonkey script to a Firefox extension</a> a while back. That this was possible, and easy, demonstrates that the Firefox extension mechanism could be made a lot simpler. I thought there was talk of doing it for FF3, but it didn't happen.

What do Firefox extensions do that Greasemonkey can't? Nothing Greasemonkey can't get around.

<ul>
  <li>Extended access - manipulating the Browser Object Model, accessing local file system, etc. All of this could be possible from a Greasemonkey script with the right APIs available. There are security implications, of course, but as long as users are aware of who can do what, it's no different from what we have now. It may be even better, due to Greasemonkey's built-in wildcard-based URL filtering, so that certain apps might only be limited to certain domains.</li>
  <li>Metadata - certain metadata is present in an extension. This could just as easily be part of Greasemonkey's metadata.</li>
</ul>

It's my hope that Google's vision for Chrome plugins is Greasemonkey on Steroids, and that this unleashes a whole new ecosystem of powerful add-ons that have until now required too much effort to build.

<img style="width:350px;" src="http://picupper.com/2008/10/20/20070108grease.jpg" />