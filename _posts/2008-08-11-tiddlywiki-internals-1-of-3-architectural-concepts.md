---
id: 472
title: 'Tiddlywiki internals 1 of 3: Architectural Concepts'
date: 2008-08-11T12:25:17+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=469
permalink: /tiddlywiki-internals-1-of-3-architectural-concepts/
dsq_thread_id:
  - "375316479"
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
(This is part 1 of a 3-part series. <a href="http://softwareas.com/tiddlywiki-internals-1-of-3-architectural-concepts">Part 1</a> introduces the internals and highlights some of the key patterns and concepts. <a href="http://softwareas.com/tiddlywiki-internals-2-of-3-list-of-javascript-files">Part 2</a> introduces each Javascript file. <a href="http://softwareas.com/tiddlywiki-internals-3-of-3-key-javascript-classes-and-files">Part 3</a> focuses on the internals of the more important classes and files.)

This is the first in a 3-part series on the internal design of Tiddlywiki. The series is more or less stream of consciousness - I'm a green Tiddlywiki developer, so I've been making these notes as I trawl through the source and learn it myself. Thanks to various people at Osmosoft for explaining some of this, and special thanks to <a href="http://jermolene.com/">Jeremy</a> for some overviews and reviewing the writing here, <a href="http://about.unamesa.org/Imtiaz">Saq</a> for a great overview on many feature, and <a href="http://fnd.lewcid.org/blog/">Fred</a> for reviewing the initially published version.

<h2>Overview</h2>

A Tiddlywiki is a collection of "tiddlers", small blocks of content typically a paragaph or so in length. At any time, a subset of these tiddlers is displayed in the UI (between zero and the total number of stored tiddlers).

A special property of Tiddlywiki is that the entire application resides in a single HTML/Javascript/CSS file (it's the quintessential SPA - <a href="code.google.com/p/trimpath/wiki/SinglePageApplications">Single-Page Application</a>). This is why you can save a Tiddlywiki locally and run it off a file:// URL and stick it on your iPod or novelty hamburger USB stick.

In the file, all the tiddlers are stored inside invisible DIVs, which are read on startup into a "TiddlyWiki" data structure. When you invoke the save feature, for example by hitting the "save changes" control, the invisible DIVs are refreshed with latest content from memory, and the entire file is written out to the hard drive.

TiddlyWiki is much more than a specialised wiki - due to its flexible architecture and the possibility of plugins, it is more like a platform. <a href="http://osmosoft.com/#Products">Examples of apps built on Tiddlywiki.</a>

<a href="http://www.tiddlywiki.org/wiki/TiddlyWeb">TiddlyWeb</a>, though not discussed specifically here, marks an important step in the future of TiddlyWiki development. It's a RESTful server of Tiddlers which would allow for great flexibility in the kinds of UIs you end up with, as well as allowing non-UI clients.

<h2>Anatomy of a Tiddlywiki</h2>

The image below shows an Tiddlywiki in editable mode. As for the UI, you can see it consists of a main area with two sidebars. The main area is a "Story" - a story is a sequence of visible tiddlers.

<a href="http://skitch.com/mahemoff/ubw2/tiddlywiki-a-reusable-non-linear-personal-web-notebook"><img style="width: 400px; height: 600px;" src="http://img.skitch.com/20080811-kkjw7cg9brkrigncj4epec43gx.jpg"></a>

A lot of this is configurable by changing special tiddlers. In particular, the tiddler called "PageTemplate" provides the overall structure, with references to other tiddlers, and "Stylesheet" the CSS styles.

<h2>Object-Oriented Concepts in Tiddlywiki</h2>

There are many ways to deal with classes, objects, and prototypes in Javascript - see <a href="http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742/ref=pd_sim_b_1/102-7069230-4404147">"Javascript: The Good Parts"</a> by Doug Crockford and <a href="http://www.amazon.com/JavaScript-Design-Patterns-Recipes-Problem-Solution/dp/159059908X">"Pro Javascript Design Patterns"</a> by Ross Harmes and Dustin Diaz.

Tiddlywiki's OO relies on the constructor function pattern, where you create new objects using the new keyword.

[javascript]
var tiddler = new Tiddler();
[/javascript]

In Javascript, <tt>new Fn()</tt> will magically does a couple of things that let us use the familiar (from C++, Java, etc.) idiom above. It sparks the creation of a blank object, then it conducts a special execution of Fn() in which <tt>this</tt> is superfrajalistically tied to the new-born object. This leads us to an idiom which is called a "constructor function" because it is a function that is both called and implemented as if it were, for the most part, a constructor in OO languages like C++ and Java. The <tt>Tiddler</tt> constructor function is defined as follows:

[javascript]
function Tiddler(title)
  {  
    this.title = title;
    this.text = "";
    ...
    return this;
  }
[/javascript]

In addition, the new Tiddler has a number of standard Tiddler methods associated with it, so I can call them in typical OO fashion, e.g. <tt>tiddler.isTagged("happy")</tt>. The implementations refer to the specific instance using the <tt>this</tt> keyword. In Javascript, this can easily be achieved via prototypes. Therefore, subsequent to the constructor definition, we encounter in Tiddler.js a menagerie of method definitions like:

[javascript]
Tiddler.prototype.isTagged = function(tag)
{
  return this.tags.indexOf(tag) != -1;
}
[/javascript]

All of the attributes above are public, but Tiddlywiki also uses closures to ensure some attributes are only available externally via declared methods. For example, the tiddlers of a Tiddlywiki is a declared as a local variable, so there's no direct reference to it outside the methods declared in the same scope.

[javascript]
function TiddlyWiki()
{
  var tiddlers = {}; // Hashmap by name of tiddlers
  this.tiddlersUpdated = false;
  ...
  this.fetchTiddler = function(title) {
    var t = tiddlers[title];
    return t instanceof Tiddler ? t : null;
  };
}
[/javascript]

The above methods will also be available on each instance created with <tt>new</tt>, just as with those declared using the prototype assignment. They are used in exactly the same way. The only difference is that all these functions are re-created with each new instance, so they will consume more memory. That's the price we pay for the encapsulation.

You will also find static methods present (i.e. global functions attached to a constructor purely for the sake of namespacing them). For example:
[javascript]
TiddlyWiki.isStandardField = function(name)
{
  return TiddlyWiki.standardFieldAccess[name] != undefined;
}
[/javascript]

Typically, a class will be contained in a single, dedicated, Javascript file (within the source code from which a Tiddlywiki is built). However, the previous example was actually contained in TiddlerFields.js rather than Tiddlywiki.js, so it seems that class definitions may be distributed across multiple files in some limited cases.

And that's how Tiddlywiki handles basic OO.

You'll also see some parts of TiddlyWiki enhancing built-in Javascript types by extending their prototype - for example, BasicTypes.js endows all Arrays with a <tt>contains()</tt> method and Dates.js sticks a <tt>getAmPm()</tt> method onto each Date that's created. Number, Array, and Date receive a dozen or so new methods.

Last but not least, there's also a healthy dose of <a href="http://en.wikipedia.org/wiki/Inheritance_(computer_science)">inheritance</a> in Tiddlywiki. Javascript inheritance is a whole new can of worms. We see an example in AdaptorBase, which serves as the base class for server adaptor subclasses. AdaptorBase looks very normal, like Tiddler above. FileAdaptor, a subclass, looks like this:

[javascript]
function FileAdaptor() {
}

FileAdaptor.prototype = new AdaptorBase();
[/javascript]

Basically, Javascript has a concept of prototype chains. The assignment means that any instance of FileAdaptor will now have all methods present in a new instance of AdaptorBase. FileAdaptor goes on to define its own methods, using the standard prototype pattern. If so inclined, it can override AdaptorBase's methods by defining them on its own prototype method. (This is why we say "new AdaptorBase()" - if we had assigned FileAdaptor.prototype to AdaptorBase.prototype, anything we set on FileAdaptor would also be set on AdaptorBase.)

<h2>URL Arguments</h2>

Tiddlywiki uses the fragment identifier pattern (<a href="http://AjaxPatterns.org/Unique_URLs">described here</a>) to provide flexible loading strategies.

Normally, the "DefaultTiddlers" shadow tiddler is used to specify which tiddlers are shown on startup. However, this can be overridden via URL params. For example, use <a href="http://www.tiddlywiki.com/#Examples">http://www.tiddlywiki.com/#Examples</a> to load with just the Examples tiddler showing. Or, for multiple tiddlers, just separate with a space (%20 in URL-5peak) <a href="http://www.tiddlywiki.com/#Examples%20Plugins">http://www.tiddlywiki.com/#Examples%20Plugins</a>. (An interesting possibility would be for Tiddlywiki to keep updating the URL to ensure its sync'd with the state of the app, so you could bookmark it at any time to save that configuration.)

But maybe you don't want to manually list all the tiddlers - instead, you might want to show all tiddlers matching some criteria. Then you'd want an automated mechanism for auto-selecting those criteria (think iTunes Smart Playlist for dramatic effect.) This would make the URL shorter, easier to understand the true purpose of the configuation, and future-proof it against any changes to the set of tiddlers we're interested in.

In Tiddlywiki, that mechanism is achieved with a URL "filter" prefix. For example, show all tiddlers with "systemConfig" tag - <tt>http://tiddlywiki.com/#filter:[tag[systemConfig]]</tt>.

Other things you can do -
  http://tiddlywiki.com/#newTiddler:tiddlername - create a new tiddler, specifying the name

The URL is modelled as a map, i.e. key-value pairs. In the case of <tt>http://www.tiddlywiki.com/#Examples%20Plugins</tt>, that's just an alias for the canonical map form, <tt>http://www.tiddlywiki.com/#open:Examples%20open:Plugins</tt>. All this is managed by the Paramifiers class.


