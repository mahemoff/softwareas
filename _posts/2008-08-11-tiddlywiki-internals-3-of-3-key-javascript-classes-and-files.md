---
id: 475
title: 'Tiddlywiki internals 3 of 3: Key Javascript Classes and Files'
date: 2008-08-11T12:53:36+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=472
permalink: /tiddlywiki-internals-3-of-3-key-javascript-classes-and-files/
dsq_thread_id:
  - "375573926"
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
(This is part 3 of a 3-part series. <a href="http://softwareas.com/tiddlywiki-internals-1-of-3-architectural-concepts">Part 1</a> introduces the internals and highlights some of the key patterns and concepts. <a href="http://softwareas.com/tiddlywiki-internals-2-of-3-list-of-javascript-files">Part 2</a> introduces each Javascript file. <a href="http://softwareas.com/tiddlywiki-internals-3-of-3-key-javascript-classes-and-files">Part 3</a> focuses on the internals of the more important classes and files.)

Concluding this series, below is a list of all core Javascript files, organised into functional groups.

<h2>main.js</h2>

main() is the function that runs onload.

Key functions:

* creates a new tiddlywiki data store (new TiddlyWiki()) - this is the collection of tiddlers users are exposed to. The store is populated using TiddlyWiki.prototype.loadFromDiv(), which loads all the tiddlers from the "storeArea" div, which is an invisible block on the page (and rendered back in nice - and visible - manner later on).
* creates a second TiddlyWiki data store to hold "shadow tiddlers" - these are "meta"/config tiddlers holding data such as CSS styling. Populated from invisible "shadowArea" div (which at compile time is defined in the Shadow/ directory).
* creates a new "Story div", a div which will show tiddlers to the user, and themes it according to config.options.txtTheme
* sets up Popup.onDocumentClick (removes popup menus when user clicks outside of the menu)
* sets up event propagation - certain tiddlers are notified when certain actions occur. The mappings are defined in refresh.js (e.g. {name: "StyleSheetLayout", notify: refreshStyles})
* sets up and renders backstage
* loads plugins (plugins are evidently supposed to set a global "plugin problem" value if a problem occurs)

General:

* calls several lifecycle event handlers as it loads - the wiki config can provide hook functions which run upon particular lifetime events
* benchmarks most of the above (the benchmarking was possibly a quick fix - relies on variables t1,t2...t10 -> this code could be optimised for conciseness using function wrappers, but maybe startup would be too slow that way).
* After initial setup ensures tiddlywiki data structures and other initialisation/config pieces are in place, it blats and shows the display with restart() and refreshDisplay().

<h2>Plugins</h2>

Tiddlywiki has a strong plugin architecture. Each plugin is included as a  regular (non-shadow) tiddler, one that must be tagged "systemConfig". (For all intents and purposes, "systemConfig" is synonymous with "plugin".) There's an example shipping with the default tiddlywiki instance on tiddlywiki.com (and a more detailed example in the source code - association/plugins/SparklinePlugin/SparklinePlugin.js). (Also of interest, <a href="http://www.tiddlywiki.org/wiki/Plugin_specs#Template">the latest plugin template at the tiddlywiki.org wiki</a>.)

{% raw %}
<div title="ExamplePlugin" modifier="JeremyRuston" created="200607271914" modified="200609212329" tags="systemConfig">
<pre>/***
|''Name:''|ExamplePlugin|
|''Description:''|To demonstrate how to write TiddlyWiki plugins|
|''Version:''|2.0.3|
|''Date:''|Sep 22, 2006|
|''Source:''|http://www.tiddlywiki.com/#ExamplePlugin|
|''Author:''|JeremyRuston (jeremy (at) osmosoft (dot) com)|
|''License:''|[[BSD open source license]]|
|''~CoreVersion:''|2.1.0|
|''Browser:''|Firefox 1.0.4+; Firefox 1.5; InternetExplorer 6.0|
***/

//{{{

// Uncomment the following line to see how the PluginManager deals with errors in plugins
// deliberateError();

// Log a message
pluginInfo.log.push(&quot;This is a test message from &quot; + tiddler.title);

//}}}</pre>
</div>
{% endraw %}

A plugin is essentially just a Javascript block which gets executed on page load. All the biosketch info is optional (although in some cases, it does effect processing, e.g. there is a check against the required TiddlyWiki version). "Just some Javascript" did you say? <a href="http://ejohn.org/blog/jquery-plugins-size-and-storage/">This post on JQuery plugins</a> by JQuery daddy John Resig is instructive. His point is that a plugin architecture needs explicit points for plugins to hook into - i.e. an API - and the existence of a plugin catalogue. Tiddlywiki doesn't have a plugin API <em>per se</em>, but is structured with plenty of extension points to naturally hook into. As for the catalogue, there's also a <a href="http://www.tiddlywiki.org/wiki/Plugins">plugin wiki area</a>, with a grander-scale plugin repo project in progress.

Incidentally, note that you don't have to register the Javascript block as you might do in some other frameworks (e.g. runOnInit(myPlugin); ). It executes automatically when plugins are loaded.

Okay, so about those plugin extension points. I'm still learning that. In the case of sparklines, the purpose is to create a new macro (e.g. <tt>&lt;&lt;sparkline 100 200 300&gt;&gt;</tt>), so it defines <tt>config.macros.sparkline.handler(place,macroName,params)</tt>, and its "output" is to populate the <tt>place</tt> element with sparkline content.

Another popular pasttime for plugin developers is szhushing the global Formatter object to shape how stuff gets rendered. e.g. if your formatter locates the built-in formatter named "heading", it could easily overwrite its handler method to MAKE ALL THE HEADINGS SHOUT AT UNSUSPECTING READERS.

To install a plugin, users usually use the Import dialog, accessible from Backstage. It's also possible to manually include plugins <a href="http://mnteractive.com/archive/how-to-install-a-tiddlywiki-plugin/">via cut-and-paste</a> into Tiddlywiki.

There's much more to be said about plugins. The bottom line is that Tiddlywiki's architecture lets you bend the core product into many things. (By "architecture", I refer to both the plugin mechanism and the flexible nature in which the overall architecture is structured.)

<h2>Tiddlers</h2>

Tiddlers are the atomic content blocks that make up a Tiddlywiki, typically about a paragraph in length. A Tiddler is simply a block of text, with extra info like a title, a list of tags, and timestamp data. There's also a <tt>fields</tt> hash where you could store any arbitrary properties. (This seems suitable for plugins, but the core also makes use of it, and I don't really get that. Even for plugins, why can't they just make new fields dynamically?)

<tt>Tiddler</tt> is a Javascript class, so you get a new instance with <tt>new Tiddler()</tt>. Internally, it uses a publish-subscribe mechanism, where a changed() method is called after any mutation. This basically ensures the <tt>links</tt> property is up to date, as <tt>links</tt> is a redundant (and presumably there for performance) collection of links inside the tiddler.

A Tiddler also has a collection of "slices", though the collection is managed by <tt>TiddlyWiki</tt> rather than <tt>Tiddler</tt>. (This relates to the fact that shadow tiddlers are mere text blocks - using Tiddlywiki to extract slices ensures shadow tiddlers can also be sliced up....and slices are a major feature of most shadow tiddlers, since they are config-related.)

There's a string-&gt;string map from name to slice. This is similar to the fields hash, insofar as it's a free-form map. In this case, though, it's something that can easily be changed by the user in real time, as the slice collection is sync'd to the tiddler content. For example: |''slicename:''|''some slice content''|. Slices allow for easily edited meta-data, e.g. a stylesheet tiddler can have a slice called "backgroundColour". Users then edit the backgroundColor slice content to set the background colour.

A Tiddler also has a set of notification handlers - this is also managed by TiddlyWiki rather than the Tiddlers themselves (again, this ensures the mechanism works for shadow tiddlers). These are listeners/observers that are notified each time tiddler is changed.

A file closely related to Tiddler is TiddlerFields.js. It actually alters the TiddlyWiki definition rather than the Tiddler definition, but in any event it deals with accessing the Tiddler's fields map.

<h2>Shadow Tiddlers</h2>

Shadow tiddlers are a particular type of tiddler. There's no separate "ShadowTiddler" class, but they are held in a separate store and treated in special ways. Indeed, shadow tiddlers aren't actually of class Tiddler (which is slightly confusing). They are simply a title-text pairing; the data structure is a map from title to text. In contrast, regular Tiddlers are mapped from title to Tiddler.

In particular, TiddlyWiki has a fallback mechanism when asked to return a tiddler - if the tiddler doesn't exist, it will attempt to revert to a shadow tiddler of the same name. Shadow tiddlers are immutable (unless you hack source code), whereas tiddlers are of course easily edited. You can override shasow tiddlers with regular tiddlers of the same name, but the original shadow still lurks (in a good way) in the background.

To see this, open an editable Tiddlywiki, choose a shadow tiddler from the right sidebar Contents menu (e.g. SiteUrl), edit it, and save it. Then re-open it to verify your changes were affected. Then delete it, and notice that it's still in the list of shadow tiddlers. When you open it yet again, you'll see it now contains the original content. (The shadow tiddler itself never changed.)

Shadow tiddlers are used for config stuff like stylesheets. The fail-safe mechanism ensures you can easily "restore factory defaults" at any time.

<h2>TiddlyWiki</h2>

A Tiddlywiki is essentially a hash of Tiddlers, keyed on their title. More precisely, it's a wrapper around this hash. Here's a (slightly refactored) look at the relevant code for managing tiddlers, which looks like any other hash wrapper:

[javascript]
function TiddlyWiki()
{
  var tiddlers = {}; // Hashmap by name of tiddlers
  ...
  this.clear = function() { tiddlers = {}; };
  this.fetchTiddler = function(title) { return tiddlers[title]; };
  this.deleteTiddler = function(title) { delete tiddlers[title]; };
  this.addTiddler = function(tiddler) { tiddlers[tiddler.title] = tiddler; };
}
[/javascript]

There is also a set of similar methods which wrap around these to provide more intelligent behaviour. e.g. createTiddler() wraps addTiddler() to provide "Add or retrieve if exists" functionality. getTiddler() wraps fetchTiddler() to ensure null is returned if no such tiddler exists. removeTiddler() wraps deleteTiddler() to delete only if the tiddler exists, and also notifies the tiddler's listeners. Most other methods also do "general stuff" with the tiddlers hash. A lot of them also run operations on behalf of Tiddlers themselves (this is mostly so it can endow shadow tiddlers - which are just strings - with certain behaviour, as mentioned in the previous section.)

<h2>Story</h2>

Story is the sovereign UI element in TiddlyWiki - its the container of all visible Tiddlers which you'll usually see occupying the main, middle, column. Theoretically, there could be more than one Story instance on the page, but I'm told that there are some hard coding shenanigans that rule it out in the project's current state. (Specifically, direct references to the "story" instance that main.js creates.) So Story is a singleton class in practice.

One gotcha here with the nomenclature - a "tiddler" inside Story.js is conceptually a DOM element, whereas in most other places its a data structure. Obviously, the tiddler UI element is a rendering of the tiddler data structure. However, the implementation isn't entirely symmetrical because the data structure has a dedicated class (Tiddler), while the UI element doesn't; tiddler rendering is handled purely by the Story class. In one case (<tt>displayTiddler()</tt>), either form is valid as the "tiddler" argument, similar to $() functions that accept either the element or the ID (<tt>title = (tiddler instanceof Tiddler) ? tiddler.title : tiddler</tt>.)

Story's key properties are a container ID, which points to the container DOM element, and an idPrefix, the prefix for all tiddler IDs. The container already exists on the page when a Story object is created to manage it.

[javascript]
function Story(containerId,idPrefix)
{
  this.container = containerId;
  this.idPrefix = idPrefix;
  ...
}
[/javascript]

Each tiddler's ID is simply <tt>idPrefix + title</tt>. You might expect an array of tiddler DOM elements, but Story doesn't need it, as it can use the DOM itself to keep track of them; the direct descendents of the Story container are the Tiddler elements. It simply uses DOM traversal techniques to iterate through all such elements, when it needs to. (There's a generic forEachTiddler function too; I could imagine there might be some value in other <a href="http://martinfowler.com/bliki/CollectionClosureMethod.html">collection closure methods</a>.)

Story contains the logic to display a tiddler. <tt>displayTiddler()</tt> decides if the tiddler is already being shown, and if not, creates a new child element with the tiddler content. It delegates to the animation engine for display.

There is also <tt>refreshTiddler()</tt> - the logic for rendering the tiddler - which is called from <tt>displayTiddler()</tt>. For flexibility, tiddlers are rendered using a template, a template which is generally contained in a shadow tiddler. There's a ViewTemplate shadow tiddler and an EditTemplate shadow tiddler - it depends on whether the tiddler is being edited.

Furthermore, there is the concept of themes, which means you can use different templates. This is handled by <tt>switchTheme()</tt>. An example of different templates is <a href="http://tiddlythemes.com/empties/TiddlyPedia.html#ViewTemplate%20EditTemplate">illustrated here in the TiddlyPedia theme</a>.

<hr>

And that concludes the three-part series. Thanks again to those who helped me gather this info (see credits in <a href="http://softwareas.com/tiddlywiki-internals-1-of-3-architectural-concepts">first article</a>). I've learned a lot about Tiddlywiki in writing it, but I still have a long way to go. There wil be more.
