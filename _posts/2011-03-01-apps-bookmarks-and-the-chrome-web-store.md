---
id: 1123
title: Apps, Bookmarks, and the Chrome Web Store
date: 2011-03-01T19:25:15+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1123
permalink: /apps-bookmarks-and-the-chrome-web-store/
dsq_thread_id:
  - "375451158"
categories:
  - SoftwareDev
tags:
  - Chrome
  - Development
---
<img src="http://farm6.static.flickr.com/5174/5466843010_2ceb08df0b_b.jpg">

A question we get a lot about <a href="https://chrome.google.com/webstore">the Chrome Web Store</a> is the distinction between apps and sites, or "aren't these just bookmarks"? Here is my take on the topic. It's not necessarily the official view, just my personal opinion to help you explore the concept further.

<strong>Most apps on the store are are indeed a link to an existing page on the web somewhere; what matters is the content on that page. <a href="http://code.google.com/chrome/apps/articles/thinking_in_web_apps.html">A successful app</a> will be visually rich, "full-screen", task-focused, and easy to start using. For example, a link to Amazon.com wouldn't work as an app, but <a href="https://chrome.google.com/webstore/detail/nielaigelomefgdoljcpfgbdbfefhdjc">Amazon Window Shop</a> does.</strong>

The fine print:

<ul>
  <li>I suggest thinking of the store as a place where you can discover great web apps. Need a photo editor? <a href="https://chrome.google.com/webstore/search?q=photo+editor">Search for it on the store</a> and you'll not only find a list of apps, but also reviews, comments, and screenshots for those apps. That preview info is much more useful than just links, when you consider that each app takes time to learn and in some cases require sign-up and payment.</li>
  <li>In some cases, apps already exist and are then submitted to the web store. That's totally fine, the important thing is if it's a good app or not. <a href="http://www.mapnificent.net/">Mapnificent</a> was an existing website, it works on multiple browsers, but was submitted to the store and has been popular with users.</li> Some apps can gain from the publicity of launching on the store at the same time as launching as a regular website, but that's a side issue. Also, apps like GMail - which were well known prior to the store launching - seem to attract more "but it's just a bookmark" reactions. I think that's just an initial reaction and will go away as users get familiar with the web store concept.</li>
  <li>In other cases, apps are developed just for the store. e.g. I think (but don't have the back story), this was the case with WeatherBug's <a href="https://chrome.google.com/webstore/detail/ihdkejbciahopmbagpnjmmkkdpfpaaak">Weather Window</a>, one of my favourite examples of a well-focused, personalised, rich app on the store.</li>
  <li>Many modern websites fall somewhere between the richness of a <a href="http://www.mapnificent.net/">Mapnificent</a> and the traditional stature of a <a href="http://wikipedia.com">Wikipedia</a> (for example). These modern sites are often good candidates for apps, but just need a little UI tweaking. So the app's manifest should point to a slightly different endpoint, which uses a different set of stylesheets, for example, which remove most of the branding and auxiliary site info (which are gratuitous since the user has already "installed" the app). It's also good practice for these sites to support single-sign on <a href="http://code.google.com/chrome/webstore/articles/authentication.html">by implementing and checking for Open ID</a>.</li>
  <li>This being the <strong>Chrome</strong> Web Store, you can assume the platform has all the latest features of HTML5 that ship with Chrome. It's great if your app also works in other browsers too, but it's not a requirement. If you're using a feature which only Chrome supports, chances are it will eventually work when other browsers introduce the feature too. The important thing is you're at liberty not to target legacy browsers (though, again, for the right kind of app, it's certainly still worth considering web standards and degrading gracefully; but when it comes to games, for example, not gonna happen).</li>
  <li>In fact, there <em>are</em> actually some differences between apps on the store and apps accessed as regular websites. Firstly, I've been talking about hosted apps here, but there are also <a href="http://code.google.com/chrome/webstore/articles/apps_vs_extensions.html">packaged apps</a>, which are a hybrid of an extension and an app, and they can do more powerful things like injecting content on web pages. e.g. <a href="https://chrome.google.com/webstore/detail/ngmmpodmhlhciagihcjpdggoihakcahf">Fiabee</a> lets you drag images into a special "Drop Images Here" region it embeds into the page at the appropriate time. Secondly, with the <a href="http://www.readwriteweb.com/hack/2011/02/chrome-apps-can-now-run-in-the.php">recent introduction of the background feature</a>, hosted apps also get some additional permissions.</li>
</ul>

All this helps to answer a related question: How long will it take to build an app? The quick response might be the ever-faithful "How long is a piece of string?", but that old pearl ducks the question, so let me make it more concrete:

<ul>
  <li>If your product is already <a href="http://code.google.com/chrome/apps/articles/thinking_in_web_apps.html">"Thinking In Web Apps"</a>, stick it in the store today. (You might like to add Open ID support if login's required and Open ID isn't supported already.) A simple way to put it in the store is Paul's <a href="http://appmator.com">AppMator</a>. <strong>Typical Effort:</strong> 60-120 minutes, including time to make <a href="http://blog.sethladd.com/2010/11/12-tips-for-great-chrome-web-store.html">a quality landing page</a>.</li>
  <li>If your website is already using modern features, has modern look-and-feel, etc., you will probably need to customise the UI a bit and maybe revamp some features. You might also consider making it work offline with Application Cache, but that's not critical at this stage. Then submit your customised app to the store. <strong>Typical Effort:</strong> 3-7 days.</li>
  <li>If your website is a traditional "static" website, with minimal JavaScript and so on, and you've decided you want presence in the store, you'll probably want to create a brand new app from scratch. Or maybe more than one, since there doesn't have to be a 1:1 relationship between apps and sites. It's actually many:many; an app can mash up multiple sites, and a site could power multiple apps (e.g. an e-commerce site could yield a product browser, a shopping cart manager, a new deals monitor, etc.; each of these is a bite-sized, task-focused app,; the best kind of app!) <strong>Typical Effort:</strong> How long is a piece of string?!! Well, it depends a lot on your existing infrastucture, e.g. do you have an easy-to-use API for your services. So depending on that, and the nature of the app, it could be anywhere from a few days to a month or more.</li>
</ul>
