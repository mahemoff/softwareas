---
id: 1377
title: Chrome Boilerplate
date: 2011-09-28T11:21:20+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1377
permalink: /chrome-boilerplate/
dsq_thread_id:
  - "428234897"
categories:
  - SoftwareDev
---
<a href='https://github.com/mahemoff/chrome-boilerplate'>Chrome Boilerplate at GitHub</a>

I made a boilerplate for Chrome extension and app development this morning. Although the Chrome docs are great, one of the pain points is you need certain fields to be filled out in the manifest, and you also must provide icons, even in development mode. And it's not really documented which size icons are mandatory, or whether it will resize. So to kickstart Chrome extensions/apps, you can use this boilerplate.

<div><pre style='font-size:10px;'><em>
This is a boilerplate for Chrome app, extension, and theme development. It
should be easy enough to get started even if you've never built a Chrome
extension before by following the INSTALLATION notes.

Most of the boilerplate is scribbed together from the docs at
http://code.google.com/chrome/extensions and the icons auto-generated at
http://faviconist.com. It's all MIT-licensed.

INSTALLATION

  The boilerplate works out of the box, so start by installing it in Chrome:

  - git clone https://github.com/mahemoff/chrome-boilerplate.git my-project-name
  - Visit chrome://extensions and expand "Development mode" (top right).
  - Choose "Load unpacked extension ..." and point to the new project directory.
  - It's installed! You should see a new button in your address bar. Click it!

CUSTOMIZATION

  By default, most things are commented out - uncomment them to make them active.

  UI Exposure:

    Your extension can be an app, an action (address bar popup), or a theme,
    but it can only be one of these. Or if it does other stuff, maybe it won't
    do any at all. So at most only one of these can be uncommented.

  Permissions:
  
    For convenience, these are mostly selected by default (except "experimental",
    as it requires you run Chrome wiht a special flag). Be sure to comment out
    what you don't need - i.e., most of them - before distributing your extension.

  Locales: 

    A basic locale setup is included, with English declared as the default
    language. This won't do any harm even if you're not planning to localize your app.

WHO MADE THIS?

  Michael Mahemoff (http://mahemoff.com). I was previously working in Google's
  Chrome team, but am no longer at Google and this is not an official
  Google/Chrome project.</em></pre></div>