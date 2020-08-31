---
id: 860
title: 'Yoink: Extracting All Scripts and Stylesheets on the Page'
date: 2010-04-26T00:14:43+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=860
permalink: /yoink-extracting-all-scripts-and-stylesheets-on-the-page/
dsq_thread_id:
  - "377040846"
categories:
  - SoftwareDev
tags:
  - Javascript
  - Project
  - yoink
---
<img src="http://pic4.picturetrail.com/VOL715/2562261/21942942/362689087.jpg" />

This here is a script that will put the code of all scripts and stylesheets into a single variable. Usage:

[javascript]
yoink(function(all) {
  console.log("scripts", all.scripts); // string array
  console.log("stylesheets", all.stylesheets); // string array
});
[/javascript]

As you can see, you have to provide a callback because this stuff is asynchronous. It downloads the files one at a time to keep things simple and without using any fancy-pants Ajax queueing library. And right now, timeouts won't be too graceful. Also, browsers will typically allow scripts and stylesheets to work cross-domain, but of course XHR won't. So any external scripts and stylesheets are unfortunately out of reach and will not be captured. This is an especially tragic circumstance in the case where they are hosted on a different subdomain. But, as they say, "hey". I don't know what that means, but, as they say, "hey".

Yoink will download inline scripts (script tags with bodies), remote scripts (script tags having a "src" attribute), inline style attributes (elements having a "style" attribute), inline style tags (style tags with bodies), and remote stylesheets (links of type "text/css").

There are several purposes. I did a quick hack version of this a while back to improve logging info; in principle, a logging method could introspect on the source tree to show extra context info (locate the log message I'm currently outputting, and then say which line it's coming from, for example).

In the case of <a href="softwareas.com/spa-hacks">Single Page Applications</a> a la TiddlyWiki, a plugin might use Yoink to inline all the remote content.

Right now, I'm more interested in using it for browser extensions, such as the Feature Creep extension <a href="http://mini.softwareas.com/a-few-browser-extensions-id-like-to-see-or-ma">I suggested</a>, to show what's happening on the page. Some of that stuff you can work out by inspecting the DOM, but other stuff ... show me the code!

Get it here - http://gist.github.com/378850. Shown below for convenience:

[javascript]
function yoink(complete) {

  var all={
    scripts: [],
    stylesheets: []
  }

  function downloadResources(urls, onComplete) {

    var resources = [];

   (function inlineResource(index) {

      if (index==urls.length) {
        onComplete(resources);
        return;
      }

      var xhr = new XMLHttpRequest();
      xhr.open("GET", urls[index], true);
      xhr.onreadystatechange = function() {
        if (xhr.readyState!=4) return;
        if (xhr.status==200) resources.push(xhr.responseText);
        inlineResource(index+1);
      }
      xhr.send();
    })(0);

  }

  var scripts = document.getElementsByTagName("script");
  var scriptSources = [];
  for (var i=0; i<scripts.length; i++) { 
    if (scripts[i].src) scriptSources.push(scripts[i].src); // remote
    else all.scripts.push(scripts[i].innerHTML); // inline
  };
  downloadResources(scriptSources, function(resources) {
    all.scripts = all.scripts.concat(resources);

    var styles = document.getElementsByTagName("styles");
    for (var i=0; i<styles.length; i++) { all.stylesheets.push(styles[i]); };
    var allElements = document.getElementsByTagName("*");
    for (var i=0; i<allElements.length; i++) {
      var inlineStyle = allElements[i].getAttribute("style")
      if (inlineStyle) all.stylesheets.push(inlineStyle);
    };
    var links = document.getElementsByTagName("link");
    var cssHrefs = [];
    for (var i=0; i<links.length; i++) {
      if (links[i].type=="text/css") cssHrefs.push(links[i].href);
    };
    downloadResources(cssHrefs, function(resources) {
      all.stylesheets = all.stylesheets.concat(resources);
      complete(all);
    });

  });

}
[/javascript]