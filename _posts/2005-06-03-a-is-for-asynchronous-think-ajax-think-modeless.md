---
id: 138
title: '&#8220;A&#8221; is for Asynchronous &#8211; Think AJAX, Think Modeless'
date: 2005-06-03T20:04:30+00:00
author: admin
layout: post
guid: http://www.softwareas.com/a-is-for-asynchronous-think-ajax-think-modeless
permalink: /a-is-for-asynchronous-think-ajax-think-modeless/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "381608618"
  - "381608618"
categories:
  - Links
  - SoftwareDev
---
Today's entry is brought to you by the letter "A". **The "A" in AJAX stands for Asynchronous**, and [CÃ©dric Savarese](http://formassembly.com/blog/ajax-not-all-about-xmlhttprequest/) cautions that many AJAX applications treat XMLHttpRequests synchronously. That is, they submit data and do something when it responds. He cautions:

> What happens really is that XmlHttpRequest is not used for what it is good at: asynchronous, behind-the-scene, access to the server, but in the context of a synchronous transaction by the user.

His solution is to get the client doing most of the work. **I agree the browser needs to do more work, but I don't think it's as simple as turning the browser into a platform for smart Javascript applications. Instead, a better solution is to <i>think modeless</i>.** The web has traditionally been a back-and-forth conversation between browser and web server. Many have pointed out that this style mirrors the old client-server mainframe applications from the '70s and '80s. Under that paradigm, the computer's drives the show. **Then came window-based GUIs and suddenly the user's calling the shots.** Everything is conceptually parallel - all the objects you see on the screen are alive, responding and communicating with each in parallel with the user's activity.

**"Modeless" is how we need to think with AJAX.** I realise the latency imposes a massive constraint on that type of thinking, but it's still the right direction to work towards. In fact, as we'll see below, the latency makes the case all the more compelling.

A GUI examples illustrates the point. Some GUIs are more modeless than others, and Allan Cooper's "About Face" described different styles of form validation in GUIs. Here are two ways you can validate a form in a desktop GUI:
+ Modal: When the user enters an invalid field, immediately pop up a dialog box, ensuring they don't proceed.
+ Modeless: When the user enters an invalid field, change its background colour and let them fix it later.

The second approach is modeless, and users generally prefer this style because it feels like they're working *with* the computer rather than *for* the computer. An AJAX live form, by analogy, might operate in two ways:
+ Modal: Each time the cursor leaves a field, go the server and validate it synchronously, popping up a dialog box and not proceeding if in error.
+ Modeless: Each time the cursor leaves a field, send an asynchronous validation request to the server, but let the user proceed and, in parallel, change the background colour (with a message perhaps) for any fields as results come back from the server. This can be be quite effective if the server provides some progress indication, as well as an indication of synchronisation status (several [AJAX patterns](ajaxpatterns.org) address this).

In both cases, the user is more free when invalid fields do not cause a halt in proceedings. In the AJAX example, the modeless case is even more compelling. Due to the performance issue, modeless form-filling will proceed much more quickly. In most cases, the fields will be invalid, so there's no major problem with the switch in attention back to any invalid fields.