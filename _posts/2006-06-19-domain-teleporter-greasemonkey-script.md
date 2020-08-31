---
id: 309
title: 'Domain Teleporter &#8211; Greasemonkey Script'
date: 2006-06-19T10:20:21+00:00
author: admin
layout: post
guid: http://www.softwareas.com/domain-teleporter-greasemonkey-script
permalink: /domain-teleporter-greasemonkey-script/
dsq_thread_id:
  - "375572980"
categories:
  - SoftwareDev
tags:
  - Amazon
  - Firefox
  - Greasemonkey
  - Javascript
  - Links
---
<b>Update:</b> As an experiment, converted this into a Firefox extension (<a href="http://www.softwareas.com/teleporter-from-greasemonkey-to-self-contained-extension">Blog Article</a>, <a href="http://mahemoff.com/project/teleporter/">Extension homepage</a>)

<a href="http://mahemoff.com/project/teleporter/domainteleporter.user.js">DomainTeleporter</a>, my first Greasemonkey script, is related to <a href="http://www.softwareas.com/around-the-amazon-in-80-milliseconds">this blog post from last April</a>:

<blockquote>
<p>
If you shop at Amazon.co.uk, youâ€™re often out of luck when it comes to reader comments. So I often find myself editing the URL, switching back and forth between .co.uk and .com. Luckily, this transatlantic adventure usually works out, as the crazy Amazon IDs match.
</blockquote>

<b>Domain Teleporter flips the location between .com and .co.uk, retaining the rest of the URL.</b> It would be nice to make it more generic - switch to an (quasi) TLD - but that would require more regexp parsing than was necessary here. Incidentally, I'd like to see a JS library that munges URLs - extract out the domain, the path, etc.

The script is configured to only run on Amazon, but you might find it useful with other sites too, in which case, change the applicable domains using the GM dialog.

<a href="http://mahemoff.com/project/teleporter/domainteleporter.user.js"><img src="http://img154.imageshack.us/img154/4238/domainteleporter6ps.png" width="500" height="260"></a>

Writing the GM script was fairly straightforward, began by copying <a href="http://diveintogreasemonkey.org/helloworld/divein.html">Mark Pilgrim's "Hello World"</a>. It's standard JS for the most part, but there was one gotcha: events don't usually work with the usual, portable, solution of "control.onclick()" - you get a "component not found" error. You must instead use addEventListener().