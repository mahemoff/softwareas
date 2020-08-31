---
id: 1459
title: 'Glenn Jones: Beyond the Page [Full Frontal Live Blog]'
date: 2011-11-11T15:59:56+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1459
permalink: /glenn-jones-beyond-the-page-full-frontal-live-blog/
dsq_thread_id:
  - "468590660"
categories:
  - SoftwareDev
---
Glenn Jones has a wicked talk showing his drag-and-drop and web intent adventures. A lot of this is very tricky and not well documented.

He kicks off with an impressive demo. Pure client-side, he drags elements from one window to another. Once dropped, the element fills with online IDs of the contact, by querying their homepage against the Open Graph API.

It gets even better when he drags a zipfile from explorer to Chrome, and expands it...and then drags from Firefox to Chrome. He also drags a vcard out from the contact to the desktop.

He mentions the [drag-and-drop
nightmare](http://www.quirksmode.org/blog/archives/2009/09/the_html5_drag.html)
and walks though the various scenarios: Dragging to desktop, dragging between
browsers, etc. You'll be able to see his code in the slides, but suffice to
say,there's a lot of ninja here. All the APIs are different and the browsers
there's a lot of ninja here. All the APIs are different and browsers vary widely.

One hack worth noting is the rarely used "type" attribute on the "a" link. By programmatically creating
a type='text/vcard', you can make Firefox download just like Chrome's new download feature.

On to [Web Intents](http://www.webintents.com/). Glenn has a demo using Web
Intents to pick a profile or a list of friends. 

[code]
&lt;intent action="http://webintents.org/save" /&gt;
intent.type="text/x-vcard"
intent.data=card;
window.navigator.startActivity(intent);
[/code]

[Mobile demo](http://codebits.glennjones.net/webintents/contact-intent.html)

For perspective, he goes way back to Lotus 1-2-3 days...these early DBs and spreadsheets succeeded because accountants suddenly had creative independence, data ownership, and portability. Something the later enterprise movement forgot about.
