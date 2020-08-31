---
id: 469
title: Injecting HTML into an IFrame
date: 2008-08-05T17:41:02+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=466
permalink: /injecting-html-into-an-iframe/
dsq_thread_id:
  - "375218330"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Ajax Patterns
  - IFrame
  - Javascript
  - Software
  - TiddlyWiki
---
Walking through Tiddlywiki source (write-up to follow), I noticed some interesting code in TiddlyWiki.js, <tt>importTiddlyWiki</tt> function.

The code takes a string and injects into an IFrame. I had talked to <a href="http://jaybyjayfresh.com/">Jon</a> a little while ago about a similar problem and was wondering about it ever since. The technique here looks like this:

It wraps the text with tags to make it an HTML document:
[javascript]
	var content = "<html><body>" + text + "</body></html>";
[/javascript]

It then introduces a new iframe to the page.
[javascript]
	var iframe = document.createElement("iframe");
	document.body.appendChild(iframe);
[/javascript]

Now comes the tricky part. You would think you could just create a new iframe element and set its innerHTML, but with iframes you must use an internal doc ument property.
[javascript]
	var doc = iframe.document;
	if(iframe.contentDocument)
		doc = iframe.contentDocument; // For NS6
	else if(iframe.contentWindow)
		doc = iframe.contentWindow.document; // For IE5.5 and IE6
	// Put the content in the iframe
	doc.open();
	doc.writeln(content);
	doc.close();
[/javascript]

Now the content is in our new iframe. We can then manipulate the content using standard Javascript...but ensuring a call like getElementById is executed against the iframe document, not the global document. (i.e. don't use the usual document.getElementById()).
[javascript]
	// Load the content into a TiddlyWiki() object
	var storeArea = doc.getElementById("storeArea");
};
[/javascript]

With this technique, you can take an arbitrary HTML string and delegate its parsing to the browser's built-in DOM engine. 