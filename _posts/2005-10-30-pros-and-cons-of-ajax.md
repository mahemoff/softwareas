---
id: 225
title: Pros and Cons of Ajax
date: 2005-10-30T02:23:27+00:00
author: admin
layout: post
guid: http://www.softwareas.com/pros-and-cons-of-ajax
permalink: /pros-and-cons-of-ajax/
dsq_thread_id:
  - "375275446"
  - "375275446"
categories:
  - HumansAndTech
  - Links
tags:
  - AjaxPatterns
  - Internet
  - Javascript
  - Links
  - Software
  - Web
  - Web 2.0
---
I just updated the [ajaxpatterns.org](http://ajaxpatterns.org) ["What's Ajax"](http://ajaxpatterns.org/Whats_Ajax) page to include more info on Ajax Benefits, and added a new section on Downsides. Have I missed any?

<hr />

<h1>Benefits of Ajax</h1>

<ul><li> <b>Web as a Platform:</b> The web is no longer just about websites that expose some information; it's increasingly being used for full-blown applications. These applications demand richer styles of interaction.
</li><li> <b>User Frustration:</b> The standard "click-and-wait" form-based model no longer suffices. Most people are now au fait with the basics of the web and are ready for something more.
</li><li> <b>Web 2.0 Zeitgeist:</b> Ajax sits well in the "Web 2.0" umbrella, with many of the Web 2.0 poster-child projects - such as flickr and technorati - incorporating Ajaxian features (having started before the "Ajax" term came about). Web 2.0 is about new ideas and the $$$ to make them happen, and Ajax is certainly creating opportunities for new breeds of applications, as well as fodder for improving existing systems. Ajax <i>is</i> the "web" in web 2.0.
</li><li> <b>Multiple Access Points:</b> Many people use more than one computer. People are using computers at home, at work, at school, in cafes. Laptops and portable hard drives offer one solution, but they are inconvenient, at risk of theft, and often not able to be plugged in. Hosting the data online is a more straightforward solution and accessing it from a rich web application is a natural fit.
</li><li> <b>Web as the <i>only</i> Platform</b> Thanks to the widespread adoption of public internet access, the so-called technology gap between countries and between socioeconomic groups is closing. Many people don't actually own a PC, but do have regular access to the web at internet cafes or schools or friends' homes. For this diverse category of user, there's no point installing applications and keeping their data locally. The web is their <b>only</b> platform.
</li><li> <b>Better Infrastructure:</b> Many homes now have broadband, and server capacities have continued to improve in the past few years. Due to frequent back-and-forth between client and server, Some Ajax applications can be hungry for both bandwidth and server capacity. Furthermore, server-side storage is cheap enough for many individuals and companies to prefer holding data online, which makes it feasible to access via a web application.
</li><li> <b>Productive Development:</b> For developers a web programming model can be far more productive than a the conventional GUI alternative. Developers only have to produce a single product for all platforms, they can upgrade the application frequently rather than in "big bang" style (have you ever seen a website version number?), they can choose whatever programming language and libraries they care for.
</li><li> <b>Browser Improvements:</b> While the basics of Ajax have been present for several years, browser improvements in areas such as XML-processing and debugging support, as well as adherence to standards, have eased the pain for the Ajax development style.
</li><li> <b>Security Concerns:</b> As security concerns have heightened, companies are now quicker to lock down desktops and forbid browser plugins. Web applications hosted on a company's intranet are therefore a boon for security, and allow for tighter monitoring and access control.
</li><li> <b>Platform Diversity:</b> The rise of Apple, combined with the ever-present desktop Linux, means that many applications must be developed in a portable way, and choosing the web platform is one popular way to achieve portability.
</li><li> <b>Browser Diversity:</b> Flock, Safari, and Firefox have joined Mozilla and Opera in offering serious alternatives to Internet Explorer which can no longer be ignored by mainstream developers. Most Ajax techniques, being based on standard browser features - albeit more modern ones - can generally be applied on all the recent browsers.
</li></ul>
<p>It's also worth noting why this information has spread through the community so quickly:
</p>
<ul><li> <b>The 'G' Factor:</b> Several prominent Google projects have been thoroughly Ajaxian, including Google Maps and GMail. When Google talks, people listen.
</li><li> <b>Simple Message:</b> Ajax is a straightforward message: all you have to do is point someone at Google Maps. It's a lot easier than explaining "the long tail" or "the folksonomy"&nbsp;:-P.
</li><li> <b>Rapid Dissemination:</b> Due to RSS, blogs, and podcasts, any worthy information is rapidly disseminated. For the reasons above, Ajax struck a chord in the community. Once a name was there for this desirable style of development, everyone wanted to talk about it.
</li></ul>

<h1> Downsides of Ajax? </h1>
<p>Ajax is a trade-off. Any developer considering its adoption should be aware of the downsides, such as:
</p>
<ul><li> <b>Limited Capabilities:</b> Some Ajax applications are certainly doing things people never dreamed were possible on the web, but there are still substantial restrictions of the web platform. For example: multimedia capabilities, local data storage, real-time graphics, interaction with hardware such as printers and webcams. Support for some of these are improving in recent browsers, some can be achieved by delegating to Flash, but many are simply not possible, and if required, would rule out Ajax.
</li><li> <b>Performance Concerns:</b> Constant interaction between browser and server can make an application feel unresponsive. There are, however, quite a few well-known patterns for performance optimisation such as browser-side caching. These usually suffice, even for fast-paced applications like stock trading, but Ajax still might not work for really time-critical applications such as machine control.
</li><li> <b>Internet Access Required:</b> The user can't access an Ajax application in the absence of a network connection.
</li><li> <b>Second Programming Language:</b> Serious Ajax applications require some knowledge of Javascript. Many developers are discovering that Javascript is actually a more capable language than at first assumed, but there is nevertheless an imposition to use a language different to that on the server-side.
</li><li> <b>Easily Abused:</b> As with any powerful technology, Ajax concepts can be abused by careless programmers. The patterns on this site are intended to guide developers towards more usable solutions, but the fact remains that Ajax isn't always be used in a manner that supports usability.
</li></ul>
