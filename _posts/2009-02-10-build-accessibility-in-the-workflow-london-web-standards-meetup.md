---
id: 519
title: Build Accessibility in the Workflow (London Web Standards Meetup)
date: 2009-02-10T10:41:28+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=516
permalink: /build-accessibility-in-the-workflow-london-web-standards-meetup/
dsq_thread_id:
  - "375574136"
categories:
  - SoftwareDev
---
I went along to the <a href="http://www.meetup.com/londonwebstandards/calendar/9507025/">London Web Standards Meetup</a> last night and attended <a href="http://www.meetup.com/londonwebstandards/calendar/9507025/">a presentation on accessibility</a> by David Owens. What I liked about this talk was David's grounded pragmatism. It was immediately apparent he makes real products in the real world. There is a good community of accessibility people with that attitude, which makes a good balance to some others who are prone to broadcasting accessibility edicts from ivory towers. These range from the naieve - the ever-popular "though shalt use alt tags" - to the loony - "javascript and video is forbidden due to accessibility regulations".

I captured a few notes, hardly exhaustive, but a few interesting points I picked up during the presentation. (As with the <a href="http://softwareas.com/clay-shirky-talk-london-ica-feb-4-2008">Shirky notes from last week</a>, please excuse the slap-dash style, this was taken on my phone.)

<hr>
<p>
Accessibility

Not just disabled, also if tired, on mobile, ill, hangover :) etc

Don't just build for disabled, make it easy for everyone... Usability and accessibility go hand in hand.

Accessibility at each stage

Visual design:<br/>
Recently changed mind about text resized widgets (three different sized As), conventional view is not to them because browsers already let users resize text, BUT be pragmatic esp where users have multiple disabilities which would make it hard to invoke zooming

Dev:<br/>
Flash, don't throw out just because not everyone can use it

Standards:<br/>
Eg consistent headings <Twitter.com/h1debate>
Heading structure

Skip links (skip to middle of page etc):<br/>
Not actually so useful for blind users as they tend to load a list of links, but useful for someone who can't mouse around easily
Access keys. Browser supported keyboard shortcuts. BBC myweb myway site is a very good source to link to, to help users understand how to use them. Also BBC use the same set across their asseys and American sites are using similar conventions so a pattern of standards is emrging (1=search etc)

Interaction:<br/>
hijax POSH first (plain old semantic html), then JS later
BUT with screenreaders how do you tell user something's changed above the part they're listening to?
<a href="http://www.w3.org/WAI/intro/aria">WAI-ARIA</a> standard is helping as a stopgap until html5 defines standard regions of the page and control types, and areas likely to update.

Colour:<br/>
Not just colour blindness but failing eyesight. (David will be posting links to some good resources he demo'd on the meetup page I believe.)

Video:<br/>
Making controls accessible and calling to and from javascript not flash based - then you have better keyboard access. Also transcribe content (good for seo too), it's dirt cheap with services like castingwords, at least for smaller content. But don't hold back on posting the video just because you're waiting for transcription.

I also had a colleague ask me to see if anything comes up about accessibility with maps and lo and behold, David demonstrated a google maps mashup which had some good accessibility work performed on it. I think he'll be posting the link on the meetup page. The main interesting thing was that all the points-of-interest are shown in a text-based list which will show if Javascript is disabled, and you can hit tab to rotate between the POIs on the map.