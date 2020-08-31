---
id: 654
title: FossBazaar at Open World Forum (OWF), Paris, Oct-2009
date: 2009-10-02T22:16:52+00:00
author: admin
layout: post
guid: http://softwareas.com/fossbazaar-at-open-world-forum-owf-paris-oct-2009
permalink: /fossbazaar-at-open-world-forum-owf-paris-oct-2009/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "383888664"
categories:
  - SoftwareDev
tags:
  - Conference
  - FOSSBazaar
  - open source
  - Osmosoft
  - Presentation
  - TiddlyGuv
---
Quick notes from <a href="http://mini.softwareas.com/fossbazaar-conference-openworldforum-october">today's FOSSBazaar event</a> at Open World Forum in Paris. Usual caveats on typos etc as I was writing these notes live.

<h2>Martin Michlmayr overviews FOSSBazaar</h2>

<a href="http://www.flickr.com/photos/37184970@N00/3974853103/" title="IMG_0069 (by mahemoff)"><img src="http://farm3.static.flickr.com/2524/3974853103_6d07f46d00_m.jpg" title="IMG_0069 (by mahemoff)" alt="IMG_0069 (by mahemoff)" width="400" height="300" /></a>

Procurement - might like to avoid, but they have a really important role to play. With open source, it's easy to ignore procurement - why go through procurement when you can download it! Great, that saved me several weeks of work, I can go home now :). But then you ship the code a few months later with GPL.

Make FOSS "business as usual" - how acquired, chosen, used, supported, updated, project tracked, licensed, mature.

FOSSBazaar to help people manage these issues. Good to have members outside of the US (Europe and maybe some now joining from Asia) as issues are different; this is the first FOSSBazaar meeting here.

FOSSBazaar for experienced users - working together to define standards and best practices

FOSSBazaar for inexperienced users - learning about open source issues, reducing the fear

Discuss, resolve, and document the "hard" issues related to adopting FOSS in the enterprise.

Question - why is HP spending money supporting the community?  Martin explains HP has some experience dealing with compliance issues. Want to share experiences, e.g. we explained how we explored Palamida; other companies might do the same with Black Duck. It's been a really good experience, talking to people who we might otherwise have not talked to.

<h2>Open Source Compliance - View of Validos. Martin von Willebreand (lawyer basedin Finland).</h2>

<a href="http://www.flickr.com/photos/37184970@N00/3974854661/" title="IMG_0070 (by mahemoff)"><img src="http://farm3.static.flickr.com/2516/3974854661_65ba09633c_m.jpg" title="IMG_0070 (by mahemoff)" alt="IMG_0070 (by mahemoff)" width="400" height="300" /></a>

Vaidos has DB of 130+ packages validated.

"Shall we use this package or not?" Validos adds legal validation

Shows DB report showing licenses being used in a package.

Talking about typical guidelines, e.g. distributing the licenses with the code. Putting license on your website isn't really redistributing it.

Showing how they prepared a document for republication. It's big, it's scary, and it's very likely necessary for legal purposes. [Kind of sad that open source gets this complex - makes me feel like just releasing all my code as public domain; losing attribution would be a shame, but the real downside would be the risk of liability if there's no warranty. It also makes me think that licenses should be embracing the web more, instead of forcing all this stuff to be repackaged - cut-and-pasting a URL would be a good start to what is a long path.]

Martin comments FOSSBazaar has been thinking about standardising some of this license declaration stuff; and there was a parallel effort recently which he's hoping to work with.

<h2>IP Tracking Methodology at INRIA</h2>

<a href="http://www.flickr.com/photos/37184970@N00/3974855815/" title="IMG_0074 (by mahemoff)"><img src="http://farm3.static.flickr.com/2493/3974855815_d300ca77dc_m.jpg" title="IMG_0074 (by mahemoff)" alt="IMG_0074 (by mahemoff)" width="400" height="300" /></a>

On the forge: 1600 projects; 400 open source.

Done various tracking and would be good to compare methodologies, work together on tools.

Discussion session - Working on a Creative Commons contract to establish relationship with contractors, ensuring they use open source the right way.

<h2>TiddlyGuv Tool (the bit with me in it)</h2>

Steve Barnes motivated the tool from his perspective as a governance administrator. I then gave a demo and explanation.

<a href="http://www.flickr.com/photos/37184970@N00/3975624236/" title="IMG_0081 (by mahemoff)"><img src="http://farm4.static.flickr.com/3055/3975624236_a1777c82d1_m.jpg" title="IMG_0081 (by mahemoff)" alt="IMG_0081 (by mahemoff)" width="400" height="300" /></a>

Feedback:

* Possible to get metadata e.g. to get XML feed. [Yes. Showed the bags/tiddlers model in the browser and how you can easily get a list of JSON or txt. Made the mistake of *not* demoing xml, which would have taken all of 5 seconds. Take off the pro-json blinkers next time!)

* Can I see which packages (components) are using a paricular license?

* What does a software policy look like? Do we need them at all. [Steve explained we probably wouldn't want to have a blanket policy like "don't use GPL", though others could; the tool lets you declare whatever policy you like.]

* It should be more about training than official policies. [I explained TiddlyGuv is intended to be a tool for developers and governance authorities to work together, share information, leave comments, etc.; not a rigid policing-the-masses weapon]

<h2>FOSSology</h2>

<a href="http://www.flickr.com/photos/37184970@N00/3975625896/" title="IMG_0089 (by mahemoff)"><img src="http://farm4.static.flickr.com/3492/3975625896_10fef4531b_m.jpg" title="IMG_0089 (by mahemoff)" alt="IMG_0089 (by mahemoff)" width="400" height="300" /></a>

Disclaimer that you need more than just tools and need other tools too.

Looks at every single file in a package - fuzzy match against a library of >400 known license.

Walks through demo. Can try online.

Many new features - email notifications, new licenses, tutorial section, cleanups.

Plans - new license analyser (based on phrases); concept of license categorisastion (e.g. "good license"/"commercial license")

Question regarding international labour organisation - what happens if a child developed code and contributed it? Do they have the legal authority to donate the code etc. Is there a child labour question? Martin notes international treaties as a similar issue - notes you're not allowed to distribute code from one country to another; how do you accept contributions across that boundary. It's a potential FUD issue people can use against open source in government.

<h2>Community Management and Project Governance: A checklist with an attitude Charles-H Schultz</h2>

<a href="http://www.flickr.com/photos/37184970@N00/3975627372/" title="IMG_0094 (by mahemoff)"><img src="http://farm3.static.flickr.com/2525/3975627372_bec3f32cf3_m.jpg" title="IMG_0094 (by mahemoff)" alt="IMG_0094 (by mahemoff)" width="400" height="300" /></a>

Good "HowTo"/tutorial presentation of governance on a particular projct.

Not just about making code available. but make it easy to find - e.g. when it's on sourceforge, but not linked easily from project page.

You never manage your community; so "community management" doesn't exist.
- fair, transparent rules and governance
- soft power
- trust employees like you trust other contributors