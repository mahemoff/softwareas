---
id: 486
title: Reflections from a TiddlyWiki Tiddler and Thoughts on a Guide for Web App Development with TiddlyWiki
date: 2008-09-21T23:40:46+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=483
permalink: /reflections-from-a-tiddlywiki-tiddler-and-thoughts-on-a-guide-for-web-app-development-with-tiddlywiki/
dsq_thread_id:
  - "375573968"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Javascript
  - TiddlyWiki
---
I've recently begun working on a project with Osmosoft, which I'll announce Real Soon Now, and have got my hands dirty with <a href="http://tiddlywiki.com">TiddlyWiki</a> to the point where I'm now able to make at least some useful functionality. You effectively get an MVC framework for free with TiddlyWiki, so as a power developer, I can see how it could let you build a certain type of app quite rapidly. Even without too much knowledge, you could use it for prototyping quite easily, just by knowing the key extension points. I figured it would be worth capturing my reflections to date.

There's a lot of documentation around on TiddlyWiki, and also some good support resources in the form of <a href="http://groups.google.com/group/TiddlyWiki">Groups</a> and <a href="irc://irc.freenode.net/TiddlyWiki">IRC</a>. What I'd like to see in addition to that is a guide for people writing "verticals" - web apps building on TiddlyWiki, rather than incremental enhancements. And also it would be good to see a cookbook or pattern collection covering the main types of plugins.

The other issue I've had, while I'm brain-dumping, is that plugin exceptions are caught at some point, with an error message shown, and <em>not</em> propagated, so they don't turn up in Firebug. I need to look into this more as I think there are ways to get better diagnostics. I would also like to get a better understanding of the startup and shutdown lifecycle. As explained in my last post, there are some techniques you can use to hook in at certain stages, though no direct support. 

I'll have an initial stab here at the kind of thing I'd like to see in a developer guide, and refine it massively at a time when I'm less of a green Tiddler, maybe on a wiki. I'm really not qualified to say too much at this stage, but I want to capture it while it's fresh on my mind. Note there's already a lot of good material along these lines on <a href="http://www.tiddlywiki.org/wiki">the TiddlyWiki wiki</a>.

<h3>Development Process</h3>

The simplest way to work is directly inside the TiddlyWiki. Locate shadow tiddlers under the "more" tab and edit them. And create new tiddlers, tag them as "systemConfig", and stick your plugin code inside them. Each time you change it, hit reload. That's a nice, simple, way to start off.

For serious development, <a href="http://www.tiddlywiki.org/wiki/Developing_and_Testing_a_Plugin">there are better options</a>. (Which I'm about to start learning.)

<h3>Extending TiddlyWiki into a Custom Web App</h3>

The way to extend TiddlyWiki is <em>not</em> to take a TiddlyWiki and start hacking the source. You can do anything you want to do via the following techniques:
<ul>
	<li><strong>Edit Shadow Tiddlers</strong> Shadow tiddlers are special tiddlers used to configure the TiddlyWiki. When you open a shadow tiddler and edit it, it saves as a regular tiddler. The original shadow tiddler remains, mainly as a safeguard, but becomes irrelevant. (I mention this because you might think there's a cascading effect, where the regular tiddler is run before or after the shadow. In fact, the regular tiddler simply replaces its shadow from the perspective of configuration.</li>
         <li><strong>Make Plugins</strong> A plugin is a tiddler tagged "systemConfig" and containing some code. The code will be executed when the wiki loads, since TiddlyWiki's built-in startup sequence looks for tiddlers marked SystemConfig and executes their content.</li>
         <li><strong>Include Plugins</strong> Include plugins from elsewhere if they are useful. You import a plugin via the PluginManager tool, accessible from Backstage. Or by cutting-and-pasting into a new "systemConfig" tiddler.
         <li><strong>Change Options</strong> Options such as Auto-Save also affect your application's behaviour. You can set them programatically using <tt>config.options</tt> at startup. Alternatively, if you have retained the options control in the sidebar, set options there and save the page.
</ul>

In addition, you may find you need more than one TiddlyWiki file to build up your web app. You might end up with a separate file for each key functional area. (I haven't seen this done, but a guide could explain how to pull in plugins and tiddlers from a common place. Possibly building on TiddlyWeb.)

<h3>Which Shadow Tiddlers to Customise?</h3>

Here's a list of shadow tiddlers you might want to customise for your app:
<ul>
 <li>SiteTitle - the contents of this tiddler are used in the header. This is an example of an uber-simple shadow tiddler. When you begin to build a vertical, you will want a header that reflects the name of your app. Similarly, you can set SiteSubtitle and SiteURL tiddlers.</li>
 <li>StyleSheet - the "StyleSheet" tiddlers lets you add some CSS rules to enhance or redefine the existing CSS based look and feel. This is a slightly more complex form of appearance customisation than the previous point. You probably don't want your app to look like a carbon copy of the original TiddlyWiki, so use these tiddlers to theme it. There are some other style-related tiddlers, like StyleSheetColors and StyleSheetLayout, but it's not recommended that you change them, because if you ever upgrade the TiddlyWiki core, any new styling will be ignored. So if there are things you want to change in those tiddlers, just create the CSS rule inside StyleSheet and it will take precedence. There is also a ColorPallette tiddler referenced by StyleSheetColors, which you *can* modify safely, and it lets you change the color scheme. In general, you won't need to override StyleSheetColors directly - ColorPallette should be sufficient.</li>
  <li>PageTemplate - the HTML for the entire page. An even more complex way to customise your app, by changing the raw page structure. Note the way this tiddler "pulls in" content other tiddlers. You can therefore change the appearance not just by changing PageTemplate, but by changing those included tiddlers. We've already met a couple of them - SiteTitle and SiteSubtitle - which simply contain a word or few in most cases. Others you'll noticed here are  MainMenu and Sidebar to reflect further options which are always present in your app.
 <li>DefaultTiddlers - a list of the initial tiddlers that show up when the page is loaded. In a web app, this would typically be a blurb, maybe embedding a video or image, and links to other tiddlers. The kind of thing you'd see in any web app, really. In this sense, TiddlyWiki provides you with a basic, customisable, layout scheme.</li>
 <li>etc.</li>
</ul>

<h3>What Kind of Plugins to Create?</h3>

Here are some examples of plugin styles:
<ul>
  <li>Macro - Your plugin defines <a href="http://softwareas.com/shout-first-tiddlywiki-plugin">a macro</a>. Users include the macro as &lt;&lt;macroname&gt;&gt; inside a tiddler, and your macro is invoked, and it typically spits out some content. You can easily make your macro apply inside all tiddlers by including it in ViewTemplate.</li>
  <li>Hijacking (aka Monkey Patching) - changing the behaviour of some code that's already in the application - either core TiddlyWiki code or another plugin you've imported. (Could expand this with specific things that are changed)</li>
  <li>Startup behaviour - <a href="http://softwareas.com/tiddlywiki-plugin-authoring-detecting-onload">Some code executed on startup</a>.</li>
</ul>

<h3>Architectural Principles</h3>

<ul>
  <li>Reuse - where a plugin already exists, don't reinvent the wheel. Reuse it. Likewise for core TiddlyWiki components. If possible, <a href="http://www.tiddlywiki.org/wiki/Dev:Best_Practices#Extending_Core_Functionality">hijack</a> (aka monkey patch) to extend it rather than directly hacking it. (<a href="http://en.wikipedia.org/wiki/Open/closed_principle">Open-Close Principle</a>).</li>
  <li>Modularity - Plugins build on each other. Don't write a single "big bang" plugin for your entire app. Break things down into logical units.</li>
  <li>Flexibility - keep the app open to further customisation from users. For example:
    <ul>
      <li>Content inside special tiddlers - Instead of hard-coding values, consider pulling them in from special Tiddlers, just like the way SiteTitle and SiteSubtitle shadow tiddlers are used. This way, a power user could easily change the value by modifying the tiddler. If it's content to be included somewhere, you would usually want to run wikify(tiddler.text) against the tiddler content, so the user can include TiddlyWiki markup. A useful concept here is "slices" - this mechanism lets you include content from just part of a tiddler, not the whole thing. See how StyleSheetColors uses ColorPallette for an example.</li>
      <li>Javascript inside special tiddlers - Most apps have critical algorithms which power users - if sufficiently authorised - might like to update ("strategy pattern" type modules). Isolate such code into special tiddlers, so someone can change those critical parts of your code without having to dive into the whole thing. If your core code has the right functions available, the tiddler content might be a kind of <a href="martinfowler.com/bliki/DomainSpecificLanguage.html">internal domain-specific language</a>.</li>
      <li>Favour macros over plugins which just charge in and change stuff. For example, if you were writing a comments plugin. The brute force approach would be to bolt on a comments area to every tiddler. But you could achieve the same thing by creating a comments macro, and then updating ViewTemplate to run the macro (ie adding <<comments>> to ViewTemplate). Power users could then have more flexibility in several ways: (a) they could remove comments or alter where they appear; (b) they could use a plugin like <a href="http://www.tiddlytools.com/#TaggedTemplateTweak">TaggedTemplateTweak</a> to ensure comments only appear for certain tiddlers; (c) they could customise the way comments are handled using parameters to the comments tag (assuming your macro accepted parameters).</li>
    </ul>
  </li>
</ul>

<h3>Key Classes and Functions</h3>

Here's a guide to the most important classes (
<a href="http://softwareas.com/tiddlywiki-internals-1-of-3-architectural-concepts">(More complete guide on TiddlyWiki internals).</a>):
<ul>
  <li>Tiddler - the data model for a single tiddler - its title (tiddler.title), content (tiddler.text), last modifier, etc.</li>
  <li>TiddlyWiki (~aka "store") - a collection of tiddlers. Typically, there is just one TiddlyWiki on the page containing all Tiddlers, called "store". Due to certain hard-codedness, it's not worth creating a separate TiddlyWiki - just use "store" to create, retrieve, update, and delete Tiddlers (the "CRUD" functions).</li>
  <li>Story (~aka "story") - a view showing zero or more tiddlers. The main display area you see on the standard TiddlyWiki page is a Story called "story". So use "story" to add and remove tiddlers being viewed.
  <li>(possibly others)</li>
  <li>window - for completeness sake, I'll note that there are certain "global" (i.e. window) functions worth knowing about.</li>
</ul>

Let's look at how those classes give our web app a model and view.

First, the model. How is CRUD handled?

Tiddlers are the atomic model unit in TiddlyWiki. You can inspect the contents using tiddler attributes:
<ul>
  <li>tiddler.title, tiddler.text, tiddler.fields, tiddler.tags. These are the title (which also acts as ID), content, custom fields map, and tags for a tiddler. To access slices, use getTiddlerSlice(). Note that shadow tiddlers aren't real instances of "Tiddler", so use getTiddlerText() to retrieve them and inspect their text. (There are also properties tracking creation, modifier, etc.)</li>
  <li>tiddler.set()</li> -update several features of a tiddler at once.
</ul>

So the "U" in CRUD - Updating - is handled primarily by setting its values.

As for creation, reading, and deleting - these go against the collection of tiddlers on the page, viz. the "store" object (an instance of TiddlyWiki). The key functions are:

<ul>
  <li>Creation - <a href="http://www.tiddlywiki.org/wiki/Dev:CreateTiddler">store.createTiddler(various, args, mostly, optional)</a> - makes a new tiddler. You might then customise it further with tiddler.set(). You might also want to display the tiddler, once created, with story.displayTiddler(title).</li>
  <li>Reading - store.getTiddler(title) - retrieves a tiddler by title.</li>
  <li>Updating - see above
  <li>Deleting - <a href="http://www.tiddlywiki.org/wiki/Dev:DeleteTiddler">store.deleteTiddler(title)</a> - deletes a tiddler by title.</li>
</ul>

You persist these changes by calling:
<ul>
  <li>saveChanges() - save changes to disk (remember, TiddlyWiki runs on a file:/// URL - using cunning manipulations normally exclusive to file:/// URLs, it modifies itself with the updated data)</li>
</ul>

Next, the view. This is mainly handled by manipulating the "story" global (as well as customising general structure and look-and-feel using the many appearance-related shadow tiddlers). You will probably want to show and hide tiddlers dynamically:

<ul>
  <li><a href="http://www.tiddlywiki.org/wiki/Dev:DisplayTiddler">story.displayTiddler()</a> and <a href="http://www.tiddlywiki.org/wiki/Dev:CloseTiddler">story.closeTiddler()</a> - introduce and remove a tiddler from the view.</li>
</ul>

Some important global functions:
<ul>
  <li><a href="http://www.tiddlywiki.org/wiki/Dev:Wikify">wikify()</a> - converts a string of marked-up TiddlyWiki content to HTML. (e.g. <tt>wikify(''xyz'')</tt> becomes <tt>&lt;b&gt;xyz&lt;/b&gt;</tt>.)</li> 
  <li><a href="http://www.tiddlywiki.org/wiki/Dev:CreateTiddlyElement">createTiddlyElement</a> - just a generic utility function to help create DOM elements (notTiddlyWiki-specific, but appears a lot if you're creating content via DOM manipulation).</li>
</ul> 

<h3>Cookbook</h3>

<ul>
  <li>Introducing a New Tiddler</li>
  <li>Using Slices</li>
  <li>Running Code on Startup</li>
  <li>Turning Auto-Save on</li>
  <li>etc etc</li>
</ul>

<h3>Testing</h3>

Using JSpec, building a test vertical etc.