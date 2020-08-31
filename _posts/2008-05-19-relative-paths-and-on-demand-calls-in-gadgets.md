---
id: 448
title: Relative Paths and On-Demand Calls in Gadgets
date: 2008-05-19T09:35:42+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=445
permalink: /relative-paths-and-on-demand-calls-in-gadgets/
dsq_thread_id:
  - "378302359"
categories:
  - SoftwareDev
tags:
  - Ajax
  - AjaxPatterns
  - iGoogle
  - Javascript
  - OpenSocial
---
<img src="http://picupper.com/2008/05/19/trafficlightsculpture.jpg"/>

A problem with the current opensocial gadget spec is that there's no relative path support. This means you end up hard-coding any references to Javascripts, CSS stylesheets, images, and services which are distributed along with your gadget.

This is not good. For example, you may have a "prod" setup and a "dev" setup. While developing, you will have to hard-code &lt;script&gt; tags and so on to hit the "dev" location, but then for production, you will want them pointing at your scripts in the production location. Likewise, you might want to ship the bundle to someone else for them to host on their own network.

You can deal with it using a pre-compiler tool - you know, using sed-like token substitution to piff in the right location. But a pre-compilation step is a messy compromise - I just want to distribute the code and be done with it. Another solution would be to output the gadget spec from a script, which would let you solve the problem in one of two ways: (a) inline common Javascripts and stylesheets so that you don't even need to link to them; (b) piff in the right location on the fly. Again, this is not ideal. It introduces a new server-side language and demands the spec server supports it. My aim here is simple distribution of gadgets - as long as you can host a tree of static files, you can serve my gadgets.

The optimal solution right now is far from ideal, but is the best way I know to do it. You use <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a> (and on-demand CSS and on-demand &lt;insert resource type here&gt;). First, you work out the gadget spec location, then you manipulate the URL to find the required Javascript, and then you pull it down using DOM manipulation.

I'm using a compressed version of something like this:
[javascript]
    var gadgetURL = _args()["url"];
    function loadScript(scriptURL, onLoaded) {
      var baseURL=gadgetURL.replace(/[a-zA-Z0-9_]+.xml(?.*)?/,"")
      if (scriptURL.indexOf("http")!=0) scriptURL = baseURL + scriptURL;
      if (debugMode) scriptURL+="?" + (new Date()).getTime();
      var script = document.createElement("script");
      script.src = scriptURL;
      if (onLoaded) script.onload = onLoaded;
      document.body.appendChild(script);
    }
[/javascript]

It's partly based on a <a href="http://groups.google.com/group/opensocial-api/browse_thread/thread/d063a9059795ac19">mailing list comment from Arne Roomann-Kurrik</a>. Massaging further, I end up with the following boilerplate block which must be cut-and-paste into each gadget to bootstrap reuse:

[javascript]
_IG_RegisterOnloadHandler(function() { var script = document.createElement("script"); script.src = _args()["url"].replace(/[a-zA-Z0-9_]+.xml(?.*)?/,"") + "../core.js"; script.onload = initialise; document.body.appendChild(script); });
[/javascript]

After dropping this at the bottom of my gadget, I know that (a) ../core.js will be pulled down and executed - it is <b>relative</b> path from wherever the gadget came; (b) initialise() will be called once core.js has been loaded. Each of my gadget's has an initialise() function which does gadget-specific initialisation. core.js is a common library and also happens to include loadScript() in case I want to pull down further Javascripts, and also loadStylesheet() so I can grab a stylesheet with relative path.

All this is not at all ideal, for several reasons:
<ol>
<li>For all the benefit of neatly using a separate Javascript file, you have to cut-and-paste boilerplate code into every page! But at least the boilerplate won't have to be changed often.</li>
<li>Performance will suffer as the script is loaded later than it should be.</li>
<li>It relies on the "url" being passed into the gadget; to my knowledge, this is not something you can definitely assume will happen, i.e. it's not mandated by the opensocial standard that the gadget receives a parameter called "url" identifying where the gadget came from.</li>
</ol>

I have requested on the opensocial spec mailing list to provide <a href="http://groups.google.com/group/opensocial-and-gadgets-spec/browse_thread/thread/50722f096c7a5746">direct relative path support</a> and the response has been positive, hopefully we'll see it soon, thus rendering large parts of this post obsolete. The solution looks to be rather neat - injecting a &lt;base&gt; tag to establish a base URL which all relative paths work against.