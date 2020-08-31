---
id: 1770
title: Graceful Degradation of Links
date: 2012-07-03T19:02:02+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1770
permalink: /graceful-degradation-of-links/
categories:
  - SoftwareDev
tags:
  - html5
  - Javascript
---
I made a bit of rookie error on a recent update. Suggestions for best practices are usually presented as fait accompli, but actually come from iterations in many cases. So I'd like to share how this one evolved. The actual refactorings were small, but it took a day of background thinking before the light bulb went off.

The feature "ajaxes in" some content when the user requests it.

<img src='http://i.imgur.com/id8f9.jpg' />

I call this component a "midi" (bigger than a simple button or line of content, smaller than a full page.) It acts as a kind of preview, where the user can open the full page by clicking on the "tablet" title on the top-left.

### Just a span

I begin thinking about the request controls as simple spans, like  etc, because I'm getting away from the usual channel "tablet" control. Tecnically, the Ajax handler could just parse the title of the using the span's innerHTML, but that would be error-prone and inflexible. For one thing, it would have to infer the owner as "featured", and that would make the component less general-purpose. So I embed the path as a data attribute:

<b>&lt;span data-path='/featured/comics/midi'&gt;comics&lt;/span&gt;</b>

Not bad. Now we just need to Ajax-request /featured/comics/midi and drop the content into this div. A one-liner using jQuery replaceAll() or similar.

### A real link

I don't deploy yet. I go to bed and test on iPad and realise this sucks for touch. With a real link, tablets will confirm it's a link when you press down on it. iPad, for example, will show a grey background and if you long-hold, open options to Open In New Tab, etc. I could try faking it with hover styles, etc., but it's unnecessary when I could just make this thing a link. So I do this:

<b>&lt;a href='/featured/comics/midi'&gt;comics&lt;/a&gt;

Much better on touch devices now.

### No, a real, real, link

Okay, but wait a sec. What if the user actually clicked on the link, or a search engine bot followed it? The link would take them to an unstyled block of content that's supposed to appear on a page. Well, I could try to detect XHR and format it nicely. But there's a better way:

<b>&lt;a href='/featured/comics'&gt;comics&lt;/a&gt;</b>

Just link to the actual thing the user is trying to preview. The JavaScript now adds "/midi" manually when performing the hijack. So the "/midi" link never appears on the site. Just as it shouldn't.

### Eeedjit. Why didn't I do this from the start?!! 

On the one hand, I made a basic error by not doing it from the start. On the other hand, I think it's a good example where the solution changes over time as you re-conceptualise the problem. I simply wasn't thinking about the "request controls" as links, and I was thinking if the user wants to open up a link in a new window, they can request a preview first, and then open it. But of course, users will indeed want to open in new window, right-click to copy the link, etc. That's really one of the great benefits of a HTML5 history architecture like this, where the links are real and not Ajax-era hashbangs. It's just that I didn't see it that way from the start.