---
id: 483
title: Frame-Busting Gadgets
date: 2008-09-16T11:58:42+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=480
permalink: /frame-busting-gadgets/
dsq_thread_id:
  - "375573950"
categories:
  - SoftwareDev
tags:
  - Add new tag
  - Ajax
  - AjaxPatterns
  - Gadget
  - iGoogle
  - OpenSocial
  - Security
---
In the questions after my @media ajax talk, Simon Willison asked about frame busting. If gadgets sit inside iframes, what's to stop them from busting the frame, i.e. replacing the container with another website. I notice he <a href="http://simonwillison.net/2007/Nov/2/opensocial/">made a similar comment</a> when OpenSocial came out. If a gadget can cause iGoogle to go away in place of another website, it could for example launch a phishing attack by presenting a mock iGoogle login page ("iGoogle has timed out. Please re-enter your username and password."). 

At a technical level, there is actually nothing to prevent this. There's no magic in the container. IFrames are about as good as it gets in modern browser for taming the gadgets, but there are still problems with that model, and one of those is the ability for iframes to bust out. I decided to create a demo of this. <a href="http://ajaxify.com/run/widgets/google/framebust/framebust.xml">The gadget is here</a>. You can drop it into iGoogle and see for yourself. <a href="http://picupper.com/video/framebust.swf">Video</a> below:

[kml_flashembed movie="http://picupper.com/video/framebust.swf" height="700" width="400" /]

(Parenthetically, the video is vertical. Why are videos always horizontal on the internets? It's a computer, not a TV! It should be just as easy to embed an dodecahedron video if that's what I fancy at the time.)

At this stage, there's no technical way around this. One possibility would be for the container to do something in the rarely-used <tt>onexit()</tt> method, which runs just before the new page is loaded. However, as I learned with <a href="http://webwait.com">WebWait</a>, which is also vulnerable to frame-busting, there's nothing you can really do at that stage, and you can't determine if the exit is happening because of a frame-busting event as opposed to the user just typing in a new URL. I suppose onexit() could still be used to log info to the server - if you knew all the times the container exits and which gadgets were present at that time, you might find certain (malicious) gadgets were present more times than you'd expect if they were present randomly. Although, I'm not sure about how reliable it is to make an Ajax call in the onexit(). (In this case, though, it would only need to work some of the time.)

In the future, the technical solution is <a href="http://code.google.com/p/google-caja/">Caja</a>, if it proves to be production-ready. Caja ensures a safe subset of Javascript, so a container like iGoogle would only ever serve a gadget if it was verified to be safe.

Until then, we have to rely on "social" mechanisms. i.e. user comments in the catalogue and manual checking by container staff. A while ago, iGoogle made it harder to add a gadget directly by URL - you basically have to use the catalogue unless you're a developer. So the catalogue is effectively acting as a whitelist - once found to be malicious, a gadget could be removed. This isn't simple though - gadgets are dynamic and the catalogue is effectively just a list of URLs. A malicious author could have their gadget added to the catalogue and then change it, so the gadgets need constant review - a highly ineffective process.

I also mentioned in the presentation that "html" type gadgets are more recommended than "url" gadgets. This is partly because with html gadgets, the container at least has some idea of what's happening inside the gadget - though not entirely, since the code can still reference external scripts and services. With "url" gadgets, what happens is entirely controlled by an external server.