---
id: 886
title: 'Offline Apps with Application Cache: Quickstart, Tips, and Deep Dive'
date: 2010-05-19T07:58:59+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=886
permalink: /offline-apps-with-application-cache-quickstart-tips-and-deep-dive/
dsq_thread_id:
  - "375276597"
categories:
  - SoftwareDev
tags:
  - html5
  - Javascript
  - Web
---
I've been mucking with AppCache, aka ApplicationCache. It's the secret sauce that lets you build offline apps, which is great for performance and fabulous for pretending to be an iPhone app when you're not.

<h3>Quickstart an Offline App</h3>

As with most HTML5 technologies, the basic usage is quite simple:
<ol>
<li><strong>Create a trivial trio of HTML, CSS, and JS files, maybe with an image or two.</strong> (Or reuse an existing toy app.)</li>
<li><strong>Link to a "cache manifest" file from your HTML file's <tt>html</tt> tag</strong> like so:
[html]
<html manifest="clock.manifest">
[/html]
</li>
<li><strong>Make the manifest file.</strong> It's just the literal phrase "CACHE MANIFEST" on the top line (I know, bit random), followed by the list of files in your app:
<pre>
CACHE MANIFEST
clock.html
clock.css
clock.js
clock.png
</pre>
</li>
<li><strong>Mark it as MIME type text/cache-manifest.</strong> If you're SSHing to a virtual host (like I did with Dreamhost), all you need here is a one-line .htaccess file:
<pre>
AddType text/cache-manifest manifest
</pre>
</strong></li>
</ol>

That's it. Now those files above will be cached locally and won't need to be downloaded again next time. To test it, load the site, shut down your net connection, and reload. It's still there innit.

It works the same on your app-phone - on iPhone or Android (or others maybe), load the site, switch to airport mode, go back to the browser and reload ... the site's still there. Where it gets really fun is making it into a regular app:
<ul>
<li>On iPhone, bookmark the site with the Safari "+" button, choose "Add to Home Screen", and the app will be sitting alongside all your other apps on the home screen.</li>
<li>On Android, bookmark the app in the browser. Hold your finger down somewhere empty on the home screen, choose add "Shortcuts" | "Bookmark", and choose the bookmark you've made.</li>
</ul>

You could do the same with any website of course, but it's particularly cool when the website is an offline one...it works just like a regular app!

<h3>Practical Tips and Troubleshooting</h3>

<h4>Purging the Cache</h4>

In practical terms, you are quickly going to come up the no. 1 problem of developing against a cache. How do you purge it whenever you update your code?

<a href="http://mdn.beonex.com/en/Offline_resources_in_Firefox">Simple.</a> You only need to make an arbitrary change to the cache manifest file, so just include a version number in the comment:

<pre>
CACHE MANIFEST
# v1
clock.html
clock.css
clock.js
clock.png
</pre>

Keep revving it up every time you change <em>any</em> file, because changing those files alone won't have any effect. And if it's getting serious, you'll want to practice the principles of DRY and continuous integration by automating this process.

<h4>Ridding yourself of Errors</h4>

An unfortunate thing happens when there's a downloading error: The whole thing silently fails. Until debugging tools get better, if you find your app's not updating, you ought to check each of the resources specified in the manifest really, really, carefully.

<h4>Cached Resources</h4>

Cache manifests are not exempt from standard caching rules, so the manifest itself, as well as other files might be cached. Pain. <a href="http://diveintohtml5.org/offline.html">A good solution</a> is to use the following Apache directives to .htaccess:
<pre>
ExpiresActive On
ExpiresDefault
</pre>

<h4>That MIME Type</h4>

Things might fail if the Cache Manifest MIME type is wrong, so use your browser's debugging tools or a service like <a href="http://web-sniffer.net/">Web Sniffer</a> to check it (thanks <a href="http://www.thecssninja.com/javascript/how-to-create-offline-webapps-on-the-iphone">CSS Ninja</a>).

<h4>The Wording</h4>

The wording can also trip you up. Be really sure it's exactly "CACHE MANIFEST" at the start of the file. Again, better debugging tools in the future will help here.

<h3>The Fancy Stuff</h3>

All of the above is enough to get up and running with an offline app, and maintaining it too. But wait, there's complexity too!

<h4>Fine Control Over What Gets Cached</h4>

The cache manifest file actually allows three kinds of resources:
<ul>
  <li><strong>Online resources that can be cached (CACHED).</strong> As shown in the example above, it's the stuff that's available for caching.</li>
  <li><strong>"Fallback" resources in case a file isn't cached (FALLBACK). </strong>These are like catch-all email addresses; any resource that's not cached, is a candidate for a fallback. There's a pattern-matching algorithm to map resources (which mightn't have been cached) to other resources (which hopefully have been cached). For <a href="http://diveintohtml5.org/offline.html">example</a>, you probably wouldn't cache every wikipedia article, so the fallback section would ensure a special "offline.html" page is shown for those missing articles. </li>
  <li><strong>Online-only resources (NETWORK)</strong> Resources which should never be cached, e.g. it would be a good idea not to cache stock prices if people were making million-dollar decisions on the back of what they see on your possibly-cached web application.</li>
</ul>

The syntax (adapted from the WHATWG example):

<pre>
CACHE MANIFEST
# a comment
# v37
# (version number unnecessary
# but recommended for cache purposes)

# the following "CACHE:" is optional;
# a special case because top of file
# is cache by default
# CACHE:
images/sound-icon.png
images/background.png
# note that each file has to be put on its own line

FALLBACK:
/ /sorry-i-am-offline.html

NETWORK:
/stocks/*
</pre>

<h4>Checking if We're Online</h4>

window.navigator.onLine ... try it now in your console (and try it again with your connection off).

<h4>Monitoring State and State Changes</h4>

What do you notice about all the app cache stuff above? It's all declarative, no Javascript. But you can go on to do extra stuff with Javascript too, via the <a href="http://www.whatwg.org/specs/web-apps/current-work/multipage/offline.html">Application Cache API</a>. (I am somewhat skeptical about the applications for this API, since simple and declarative is the way to go for something as potentially hairy as offline...but that's for another rant.)

The window is effective tied one-to-one to the cache object, so you can just access the cache with window.applicationCache. For example, you can get cache state with window.applicationCache.status, try it now in your console. It will probably be zero...the possible values range from 0 to 5, representing:
UNCACHED, IDLE CHECKING, DOWNLOADING, UPDATEREADY, OBSOLETE. (These constants are also available on the cache object, i.e. window.applicationCache.UNCACHED is 0.)

There are also event handlers to monitor event state: onchecking, onerror, onnoupdate, ondownloading, onprogress, onupdateready, oncached, onobsolete.

<h4>Forcing Updates</h4>

applicationCache.update() will force an update, i.e. start downloading the application again if the manifest has changed. However, it won't suddenly  switch over after downloading. To do so would be to pull the rug from under your live, running, application. It will be there next time. But if you do want it right away, use applicationCache.swapCache().

<h4>Offline Mobile Apps: It's More than Application Cache</h4>

Application cache certainly is a critical feature of mobile apps; it's a basic user expectation that a mobile app starts right away, unlike a complex web app which must be downloaded. However, there are other things too. For example, offline storage. That's another feature of HTML5, comes in many incaranations, and something for another day. The other really big deal is the UI. Of course, you need to simulate certain UI features of the native apps if you want your web app to go native. Hence, libraries like IUI, jQTouch, and Apple's secret PastryKit. On the input side, your UI must also <a href="ajaxian.com/archives/mouseovers-on-touch-devices">handle touch events</a>, something some of the aformentioned brand of libraries will support. Finally, there will be specific features of the platform that can help; <a href="http://ajaxian.com/archives/iphone-full-screen-webapps">for example</a>, setting the home screen icon and going full-screen so the browser chrome doesn't show up.