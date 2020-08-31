---
id: 529
title: 'Meeting with Aptana&#8217;s Kevin Hakman &#8211; Talking Jaxer'
date: 2009-04-09T22:51:15+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=526
permalink: /meeting-with-aptanas-kevin-hakman-talking-jaxer/
dsq_thread_id:
  - "378641160"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Aptana
  - Firefox
  - Javascript
  - Jaxer
  - Mozilla
  - Server-Side Javascript
  - Web
---
<a href="http://www.aptana.com/jaxer"><img src="http://img83.imageshack.us/img83/572/jaxerlogowhitebg.jpg" /></a>

Regular readers of this blog will know <a href="http://softwareas.com/server-side-javascript-hope-and-opportunity">I</a> am a <a href="http://softwareas.com/phobos-server-side-js-redux">big fan</a> of <a href="http://softwareas.com/the-javascript-grid">Javascript</a> on the <a href="http://softwareas.com/server-side-hosting-options">server</a>. Through its <a href="http://www.aptana.com/jaxer">Jaxer</a> project, Aptana has been at the forefront of the server-side Javascript renaissance. As I'm in SF right now (mail or tweet me if you'd like to meet up), I was pleased today to be able to catch up with Kevin Hakman, a great talent in the Ajax world who runs community relations and evangelism for Aptana.

I wanted to get an overview of the state of Aptana and Jaxer, and also understand how it might be used in a <a href="http://tiddlywiki.org">TiddlyWiki</a> context to help with accessibility.

We discussed a range of things Jaxer - I will list them below. Kevin reviewed a draft of these points and gave me some links and corrections.

<ul>
       <li>Jaxer - as you probably know, Jaxer is an Ajax engine. It's server-side Javascript, but more than that, you can perform DOM manipulation on the server, and then it spits out HTML from there. Very exciting for all the rasons I've mentioned in previous blog posts - using a single language, making proxied cals from client to server, etc. The great thing about Jaxer is it's open source - you can download a version with Apache that "just works" - download, install, and start the server in one click and the sample apps are up and running. Aptana runs a cloud host for Jaxer (as well as Rails/PHP etc), so you can host with them if you don't want to host it yourself. They have some interesting value-adds around their host, like support for different environments (dev/test/etc with different parameters, such as extra debugging), which you can easily spin out and turn off again.</li>
	<li>ActiveJS - <a href="http://activerecordjs.aptanacloud.com/">ActiveJS</a> is a Jaxer-powered framework modelled on Rails and close to beta. The most mature part is ActiveRecordJS (ORM), but there is now ActiveView and ActiveController as well. As with Rails, you can use them independently. This is exactly <a href="http://softwareas.com/the-javascript-grid">what I've been hoping for</a> and it sounds like it's mature enough to start hacking against. Kevin is realistic about uptake and expects it to be a long process.</li>
        <li>Microformats - Kevin directed me to this <a href="http://www.codegobbler.com/one-form-many-uses-server-side-jquery-jaxer">this Jaxer project</a> which filters parts of a form depending on who is viewing it. You just use a different class name to indicate who can view what, and the server chooses which parts to output. This got me thinking about microformats and how Jaxer could help render them - with a single library, dynamically in the browser and statically from the server. There are a number of microformat libraries which might already be useful sitting in a Jaxer server.</li>
        <li>TiddlyWiki - Taking TiddlyWiki based apps and using Jaxer to make them come statically from the server. Since Jaxer supports DOM manipulation, it should certainly be possible. Kevin said accessibility is certainly an argument for Jaxer, though there's no significant demo to date, so a TiddlyWiki project would make a good demo. His intuition is that it will be a 90-10 - 90% straightforward, the remaining 10 will cause some complications. Would definitely make an interesting project to do a simple version, e.g. initially just get Jaxer to output each Tiddler, showing title and wiki markup.</li>
        <li>Demo app - <a href="http://tv.aptana.com/">Aptana TV</a> is implemented in Jaxer+ActiveJS and there are plans to open source the implementation and make it Jaxer's "Pet Store".</li>
        <li>Interoperating - Jaxer can interoperate with other languages using browser extensions/plugins, since the server is basically Firefox; these are not extensions users have to install, but act as enhancements to the server. Just as a user can install a plugin to Firefox so web apps can make calls to Java for example, a developer can patch the server with the same plugin (or similar, but with the same API anyway?). Kevin said most of these kinds of components are <a href="http://www.mozilla.org/projects/xpcom/">XPCOM</a>, but I guess Jaxer should accept regular Firefox extensions and even Greasemonkey scripts. <a href="http://www.aptana.com/blog/pcolton/jaxer_and_dot_net ">DotNet COM example</a>. In a simpler sense, you can call out to other languages using the OS command line. <a href="http://www.codegobbler.com/how-execute-server-side-processes-jaxerprocess">System commands</a> have always been possible from the Jaxer server.</li>
        <li>FF bugs - Jaxer shares the Firefox's bug set and fixes, when you think about it!</li>
        <li>Performance - Likewise, Jaxer benefits from all the stuff you read about sky-rocketing Javascript performance in the browser. Jaxer will be inheriting the performance boost from TraceMonkey promising to be silly-fast at <a href="http://arstechnica.com/open-source/news/2008/08/firefox-to-get-massive-javascript-performance-boost.ars">20x to 40x speed improvements for JS</a> according to Moz.
</ul>