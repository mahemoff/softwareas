---
id: 245
title: Host-Proof Authentication?
date: 2005-11-30T09:53:52+00:00
author: admin
layout: post
guid: http://www.softwareas.com/host-proof-authentication
permalink: /host-proof-authentication/
dsq_thread_id:
  - "375572776"
  - "375572776"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Javascript
  - Links
  - Remoting
  - Security
  - XMLHttpRequest
---
Abe Fettig's done some important experimenting to arrive at a [direct remoting technique](http://fettig.net/weblog/2005/11/28/how-to-make-xmlhttprequest-connections-to-another-server-in-your-domain/), one which **bypasses the need for a [Cross-Domain Proxy](http://ajaxpatterns.org/Cross-Domain_Proxy) and doesn't rely on cross-domain [On-Demand Javascript](http://ajaxpatterns.org/On-Demand_Javascript)**. Compared to the latter technique, Abe's idea is more functional, because you get the power, expressivity, and bidirectional capability of XMLHttpRequest, as opposed to the On-Demand Javascript hack, which only allows downloading, though you could perhaps pass CGI arguments with the script request, or use one of the image/stylesheet hacks to get information in the other direction.

**If we can bypass the server. then we can consider the idea of Host-Proof Authentication.** It's based on Richard Schwartz's [Host-Proof Hosting](http://smokey.rhs.com/web/blog/PowerOfTheSchwartz.nsf/d6plinks/RSCZ-6C5G54) idea, where [encrypted data is decrypted on the fly in the browser](http://ajaxpatterns.org/Host-Proof_Hosting). In similar vein, **if you needed third-party authentication, these remoting hacks are one way to keep your password away from the prying eyes of the server host**. A while back, one of the internet banks (egg?) copped it for asking users to give them all their cusomter IDs, passwords, etc., so they could provide a one-stop-shop service. Maybe Host-Proof Authentication would be a better approach - if not automated, a portal could be set up to allow users to shuffle funds around within the browser.

Back here on Earth, I wouldn't in reality use Host-Proof Authentication for a critical application - not without a lot more consideration - because there are two reality checks:

* **Host-Proof Hosting is far from perfect**- Alex Russell has noted it's vulnerable to script injection attacks. See the comments in the above links for more on that. Similar comments apply to Host-Proof Authentication.
* **All these direct remoting techniques rely on some form of co-operation with the external server.** e.g. Abe's technique requires it to explicitly set the <tt>document.domain</tt> property; On-Demand Javascript requires it to expose appropriate scripts; image remoting requires the script to recognise any variables and output an invisible pixel; etc. The external API would have to explicitly let the browser perform remote authentication.
