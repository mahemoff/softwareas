---
id: 590
title: Towards A Single Page Application Framework
date: 2009-08-18T02:02:57+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=590
permalink: /towards-a-single-page-application-framework/
dsq_thread_id:
  - "375269080"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - JQuery
  - Project
  - SPA
  - TiddlyWiki
---
Tonight, I was thinking of making a Twitter app to manage my various accounts (I have ~dormant accounts related to projects like @webwait and @listoftweets). The app would be holding username and password details for each of these accounts, so it made sense to build it as a <a href="http://en.wikipedia.org/wiki/Single_page_application">Single Page Application</a> (SPA). This way, a more paranoid user could always keep the app in their local file system, while a less paranoid user could always stick the file on a protected server somewhere, having configured all the username-password details.

TiddlyWiki is a framework for developing SPAs. One might say it's <em>the</em> framework for developing SPAs, since there are no prominent alternatives. So my obvious choice was a TiddlyWiki. However, not too long ago, the TiddlyWiki core guys extracted out the secret sauce for SPAs: the ingenius bit of code that saves files without requiring any browser extensions. (I've tried to explain this to people and it always leaves even the most brilliant minds a little dumbstruck, but yes TiddlyWiki demonstrates there are pragmatic hacks that can be used to read a file into the browser and then write it out again.) I was keen to explore this saving mechanism, so experimentation ensued.

The file management techniques ship conveniently in a JQuery plugin, <strong>jQuery.twFile</strong>. There is a <a href="http://jquery.tiddlywiki.org/twFile.html">basic demo which lets you edit the entire text and save it</a>. The demo confused me at first - because it was editing the entire body of the file, I wasn't sure how to translate that info into what I, as an application developer needed. The demo is useful for framework developers understanding the plugin, but less so for application developers. So I extracted it into a demo that is still minimalistic, but closer to the kind of thing you'd do in an application.

<a href="http://project.mahemoff.com/spa-demo.html">The SPA demo is here.</a>

<a href="http://project.mahemoff.com/spa-demo.html"><img style="width: 400px; border: 1px solid #999;"  src="http://img.skitch.com/20090818-xy1n926xgpfdbaua3x4typ4qfb.jpg" /></a>

Once I did that, I realised what's required is a SPA framework. In practice, most developers using twFile will be keeping all the HTML, CSS, and Javascript in a single file, so it's possible to build a higher-level abstraction on twFile, so that developers can focus only on the content. I built the demo in a way that distinguished what was boilerplate framework code and what was application-specific HTML, CSS, and Javascript.

It was all still in one file, and that's fine for many developers - you can give the developer the file, tell them "edit these bits", and they can come up with something functional. I decided to extract things further though, and <a href="http://mini.softwareas.com/jinja-python-templating-lib-has-a-very-nice-w">found the Jinja templating framework to be useful here</a>. Jinja has a concept of template inheritance, so you can easily build up an "include" system.  The net effect is I was able to encapsulate SPA logic in a single file, which was passed through a Jinja processor to produce the executable HTML document.

The basic SPA logic is shown below:

<!-- {% raw %} -->
{% extends "spa-template.html" %}
{% block title %}JQuery SPA demo{% endblock %}
{% block css %}
  etc etc
  body { background: black; padding: 0; margin: 0; font-family: Gill Sans, sans-serif; }
  h1 { background: white; color: black; padding: 10px 10px 0; margin: 0; height: 52px; }
{% endblock %}
{% block html %}
  <h1>
  <img id="logo" src="data:image/jpeg,%FFetc etc"/>
    <span id="title">JQuery-SPA Demo</span>
  </h1>

  <div id="main">

    <ol>
      <li>Save this file to your local file system and open your local copy in the browser (using a file:/// URI). The browser might ask for special permission for this document, and you will need to grant it.</li>

      <li>Type your message: <input id="message" value="change me"></input></li>

      <li>Save this page: <input id="saveButton" value="Save" type="button"></li>

      <li>Hit shift-reload to perform a clean reload the page and observe that your message has been saved.</li>
    </ol>

    <h3>What is this?</h3>

    <p>This is a demo of an experimental Single Page Application I am building atop <a href="http://jquery.tiddlywiki.org/twFile.html">jQuery.twFile</a>, the file saving plugin extracted from TiddlyWiki. Forked from <a href="http://jquery.tiddlywiki.org/twFileDemo.html">this twFile Demo</a>. Only tested on Firefox for now.</p>

  </div>
{% endblock %}
{% block javascript %}
    $.spa.save = function(text) {
      return text.replace(/<input id="message".*?></input>/,
              '<input id="message" value="'+$("#message").val()+'"></input>');
    }
{% endblock %}
<!-- {% endraw %} -->

So it contains separate HTML/CSS/Javascript blocks. Probably not a good engineering practice (though it doesn't impact on the end-user experience, which is always a single file), but it's convenient for now. The key SPA logic is here:

[html]
      <li>Type your message: <input id="message" value="change me"></input></li>
      ....
    $.spa.save = function(text) {
      return text.replace(/<input id="message".*?></input>/,
              '<input id="message" value="'+$("#message").val()+'"></input>');
    }
[/html]

As an app developer, all you have to do is override $.spa.save (which in retrospect should be renamed as it doesn't actually perform the save). This function receives the text of the file as it was stored on disk when the page loaded. It must then return the text that should be saved to disk. Thus, it must store application state in HTML, probably by performing some kind of substitution.

Having put this together, I'm keen to proceed with the envisioned Twitter app. It's not yet clear if there's any mileage here over a regular TiddlyWiki, but as someone who is more familiar with starting apps from a blank HTML page (or a simple <a href="http://projectdeploy.com">Project Deploy*</a> template), it might end up being a more familiar way to kick an app off. Watch this space.
