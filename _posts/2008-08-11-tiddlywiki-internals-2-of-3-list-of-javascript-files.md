---
id: 473
title: 'Tiddlywiki internals 2 of 3: List of Javascript Files'
date: 2008-08-11T12:45:10+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=470
permalink: /tiddlywiki-internals-2-of-3-list-of-javascript-files/
dsq_thread_id:
  - "375573919"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Code
  - TiddlyWiki
  - Walkthrough
  - Web
  - Wiki
---
(This is part 2 of a 3-part series. <a href="http://softwareas.com/tiddlywiki-internals-1-of-3-architectural-concepts">Part 1</a> introduces the internals and highlights some of the key patterns and concepts. <a href="http://softwareas.com/tiddlywiki-internals-2-of-3-list-of-javascript-files">Part 2</a> introduces each Javascript file. <a href="http://softwareas.com/tiddlywiki-internals-3-of-3-key-javascript-classes-and-files">Part 3</a> focuses on the internals of the more important classes and files.)

Continuing the series, below is a list of all core Javascript files, organised into functional groups.

<h3>Initialisation</h3>

<ul>
<li><strong>main.js</strong> Runs the initialisation sequence.</li>
<li><strong>Paramifiers.js</strong> Handles URL params.</li>
</ul>

<h3>Generic (Non-Animation)</h3>

<ul>
<li><strong>BasicTypes.js</strong> Augments built-in Javascript Number and Array.</li>
<li><strong>Crypto.js</strong> Crypto functions. (Tiddlers can generate fingerprints.)</li>
<li><strong>Dates.js</strong> Augments built-in Javascript Date class.</li>
<li><strong>Dom.js</strong> Supports DOM manipulation.</li>
<li><strong>FileSystem.js</strong> </li>
<li><strong>Strings.js</strong> Augments built-in Javascript Number and Array.</li>
<li><strong>Http.js</strong> Supports XmlHttpRequest based remoting.</li>
<li><strong>RGB.js</strong> CSS colour manipulation.</li>
</ul>

<h3>Generic (Specifically Animation)</h3>

See also <a href="http://ajaxpatterns.org/One-Second_Mutation#TiddlyWiki_2">(2005) TiddlyWiki animation write-up.</a>

<ul>
<li><strong>Animator.js</strong> Runs the dynamic flow of stepping through an animation, delegating to specific strategies.</li>
<li><strong>Morpher.js</strong> Morphing animation strategy. Cool - smoothly animates between two CSS styles.</li>
<li><strong>Scroller.js</strong> Scroller animation strategy. Scrolls window to show an element. (The way the page smoothly scrolls to show a tiddler when you click its link).</li>
<li><strong>Slider.js</strong> Slider animation strategy. Slides elements opening and closed (e.g. Closing tiddlers or the Options box on right sidebar.).</li>
<li><strong>Zoomer.js</strong> Zoomer animation strategy (the way a tiddler "jumps out" from its link).</li>
</ul>

<h3>Tiddlywiki-Specific Utilities</h3>

<ul>
<li><strong>FormatterHelpers.js</strong> Utilities specifically for Formatters.</li>
<li><strong>Refresh.js</strong> Mechanism for notifying and updating elements based on changes, e.g. if stylesheet shadow tiddler is updated.</li>
<li><strong>Utilities.js</strong> Miscellaneous TiddlyWiki-specific utility functions.</li>
</ul>

<h3>Data Structures</h3>

<ul>
<li><strong>Tiddler.js</strong> Data structure representing a tiddler, i.e. a block of text with a title.</li>
<li><strong>TiddlerFields.js</strong> Augments TiddlyWiki to manage tiddler fields.</li>
<li><strong>TiddlyWiki.js</strong> Data structure representing a collection of tiddlers.</li>
</ul>

<h3>Data Import/Export</h3>

<ul>
<li><strong>AdaptorBase.js</strong> Adaptors convert from various wiki formats (e.g. Mediawiki) to TiddlyWiki. This is the base class for Adaptors.</li>
<li><strong>FileAdaptor.js</strong> Subclass of AdaptorBase which reads the default/standard Tiddlywiki format.</li>
<li><strong>Import.js</strong> Macro to import tiddlers from another Tiddlywiki.</li>
<li><strong>LoaderSaver.js</strong> Converts between HTML and a list of tiddlers. (I think the main purpose is to get a clean HTML list of tiddlers.)</li>
<li><strong>Saving.js</strong> Saves the Tiddlywiki - main case is serialising everything to DOM elements and saving to local file system.</li>
<li><strong>SavingRSS.js</strong> Serves Tiddlywiki as RSS format (e.g. <a href="http://www.tiddlywiki.com/index.xml">TiddlyWiki.com RSS feed</a>) showing time-sorted list of recently updated tiddlers.</li>
<li><strong>Sync.js</strong> Syncs </li>
<li><strong>TW21Loader.js</strong> Standard implementation of LoaderBase (defined in LoaderSaver.js).</li>
<li><strong>TW21Saver.js</strong> Standard implementation of SaverBase (defined in LoaderSaver.js).</li>
</ul>

<h3>Strategies</h3>

This is a broad category of options and control-type functions. The control-type functions are here because they are designed using flexible mechanisms which make them easily overrideable by plugin developers.

<ul>
<li><strong>Config.js</strong> General Tiddlywiki config - controls capacities, names of shadow tiddlers, which options can be set, other stuff.</li>
<li><strong>Commands.js</strong> Handlers for menus and toolbar.</li>
<li><strong>Macros.js</strong> Defines built-in macros.</li>
<li><strong>Formatter.js</strong> Formatters are strategies for locating regexp patterns in the wiki text (wiki words, image URLs, etc.) and rendering them.</li>
<li><strong>Options.js</strong> Options are cookie-based preferences. The user can generally set them directly on the Tiddlywiki UI. This is in contrast to Config.js settings, which are fixed unless the uswer cares to dive into the source code.</li>
<li><strong>Wikifier.js</strong> </li>
</ul>

<h3>UI Elements</h3>

<ul>
<li><strong>Backstage.js</strong> The backstage space at the top of the page, with access to advanced features and acting as an escape route after over-enthusiastic bouts of customisation.</li>
<li><strong>ListView.js</strong> A table-like list, e.g. shows all options when you hit Backstage|Tweak.</li>
<li><strong>Manager.js</strong> Plugin manager (accessible from Backstage|Plugins)</li>
<li><strong>Messages.js</strong> Simple status notifications.</li>
<li><strong>NewTiddler.js</strong> Macro for a new tiddler, e.g. when user hits "New Tiddler" menu option, and also new journal.</li>
<li><strong>Popup.js</strong> Popup menu (e.g. when you click on the name of a tiddler in the list of shadow tiddlers).</li>
<li><strong>Search.js</strong> Search implementation - allows user to search for a term.</li>
<li><strong>Sparkline.js</strong> Generates CSS based <a href="en.wikipedia.org/wiki/Sparkline">sparklines</a> graphic.</li>
<li><strong>Story.js</strong> Manages the container of all visible tiddler UI elements.</li>
<li><strong>Tabs.js</strong> A UI element for handling tabs.</li>
<li><strong>Toolbar.js</strong> The toolbar shown in the top of a tiddler (with "close", "close others" etc controls - or "done"-"cancel"-"delete" if open).</li>
<li><strong>Wizard.js</strong> Multi-step wizard UI framework.</li>
</ul>

<h3>Miscellaneous</h3>

<ul>
<li><strong>Deprecated.js</strong> Deprecated functions.</li>
<li><strong>Guide.js</strong> A short readme file.</li>
<li><strong>Lingo.js</strong> internationalisation-localisation support - contains string keys and their English values.</li>
<li><strong>Upgrade.js</strong> Support for upgrading Tiddlywiki vgersion.</li>
<li><strong>Version.js</strong> Short file with info about this version of Tiddlywiki.</li>
</ul>
