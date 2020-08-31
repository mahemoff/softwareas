---
id: 315
title: 'Dojo Gotcha &#8211; Initialization with window.onload'
date: 2006-06-25T12:19:15+00:00
author: admin
layout: post
guid: http://www.softwareas.com/dojo-gotchas
permalink: /dojo-gotcha-window-onload/
dsq_thread_id:
  - "375573001"
categories:
  - SoftwareDev
tags:
  - Dojo
  - Javascript
  - Links
---
I've been playing with Dojo, specifically the rich text editor, and came across a Gotcha in setting up the whole thing, which isn't documented too clearly. Specifically, Dojo needs its own window.onload - <b>if you have your own window.onload (as you probably do if you need any initialisation), it will conflict with Dojo!!!</b>

The solution is <a href="http://an9.org/ddq/">described here</a> (though it seems Dojo changed a property name a few months ago, from baseRelativePath to baseScriptURI). This is working for me - in my HTML:

[html]
<head>
	<title>My App</title>
	<script type='text/javascript'>
			var djConfig = {
	    	baseScriptURI: "/ddq/js/dojo/",
	      isDebug: true
	    };
    </script>
	 <script type="text/javascript" src="/javascripts/dojo.js"></script>
	 <script type="text/javascript" src="/javascripts/myapp.js"></script>
</head>
[/html]

In myapp.js:
[js]
dojo.require("dojo.event.*");
dojo.event.connect(window, "onload", myappInit);

function myappInit() {
    alert("Okay, here we are in the old window.onload and it's still running :-)");
}
[/js]

It might be a good idea for the Dojo crew included some explanation of this in the standard heres-how-to-setup-dojo.js-intro docs. Maybe someone with in-depth knowledge of Dojo could infer that window.onload must be used by Dojo, but the average programmer taking Dojo a spin won't.

Links:

* <a href="http://dojotoolkit.org/pipermail/dojo-checkins/2006-May/006632.html">I'm not the only person to be caught out by this</a>
* <a href="http://blog.innerewut.de/articles/2006/05/22/dojo-and-rails-or-better-dojo-and-the-base-relative-path">Setting up Rich Text Editor under Rails</a> Covers some issues with relative paths

Dojo. Awesome framework. Bring on the doco.