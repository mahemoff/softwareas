---
id: 429
title: 'Shindig Architecture: Java Gadget Classes'
date: 2008-02-25T21:56:46+00:00
author: admin
layout: post
guid: http://softwareas.com/shindig-architecture-java-gadget-classes
permalink: /shindig-architecture-java-gadget-classes/
dsq_thread_id:
  - "375237521"
categories:
  - Links
  - SoftwareDev
tags:
  - Gadgets
  - Links
  - Shindig
  - Shindigging
  - Widgets
---
This is the first of an open series on the architecture of <a href="http://incubator.apache.org/shindig/">Shindig</a>, the new open-source gadget/widget framework project. As mentioned here earlier, this project is building something similar to <a href="http://www.google.com/ig">iGoogle</a>, i.e. an environment for serving gadgets, a run-time environment for the gadgets to operate in, and a gadget container (as well as OpenSocial support).

I'm currently digging into Shindig's architecture and will document my progress.

For the record, there's not much discussion of Shindig's architecture to date. The most useful summaries I've seen are a couple of notes on the mailing list:

* http://mail-archives.apache.org/mod_mbox/incubator-shindig-dev/200801.mbox/%3Cab5e78ed0801222049n4765d16ar6ba133464776b99f3@mail.gmail.com%3E
* http://www.mail-archive.com/shindig-dev@incubator.apache.org/msg00369.html
* http://trac.hyves-api.nl/hyves-api/wiki/ShindigStarted

Also, be aware that Shindig has server-side implementations in both Java and PHP, and potentially more languages in the future. I'm focusing on Java at this time.

I'll be tagging each of these articles with "shindigging" (as well as "shindig", a general tag for anything on this blog about shindig). Thus, you'll be able to find a full list of articles from <a href="http://softwareas.com/tag/shindigging">http://softwareas.com/tag/shindigging</a>.

<h3>Java Gadget Server</h3>

I've walked through each file in the Java gadget server, in the main package - org.apache.shindig.gadgets and taken a <b>very raw</b> set of notes on each file / public class, as well as sketched a quick summary of the process. I'll refine all this later.

<h3>Java Gadget Server - Tracing from gadget spec to page content</h3>

A gadget server takes an XML file on a server somewhere and converts it to some HTML/JS/etc content inside an iframe. After looking at org.apache.shindig.gadgets, the Java gadget server achieves this task as follows.

<ul>
<li>GadgetServer is invoked from the web app to render a gadget whose spec sits at a URL</li>
<li>GadgetServer uses CacheLoadTask to load the _Gadget_ object if possible</li>
<li>If not found, GadgetServer uses SpecLoadTask, which uses RemoteContentFetcher, to grab the Spec.</li>
<li>GadgetSpecParser converts the XML string into a GadgetSpec, which is a Java representation of the XML spec.</li>
<li>Gadget constructs itself from a combination of the GadgetSpec and the preferences.</li>
<li>GadgetServer passes Gadget to each required GadgetFeature (going by the required features declared in the spec). These GadgetFeature objects perform some kind of transformation on the Gadget - typically they add one of more JS libs to it (a gadget has a list of JS libs).</li>
<li>At this point, classes in the http package kick in to render the Gadget object, of which more in a different blog post.</li>
</ul>

<h3>Java Gadget Server - Files / Classes in org.apache.shindig.gadgets (raw notes)</h3>

BasicGadgetBlacklist.java -  [part of GadgetServerConfig] dumb implementation of GadgetBlacklist - file based

BasicGadgetDataCache.java - dumb implementation       of GadgetDataCache - Just a hashmap

BasicGadgetSigner.java - dumb implementation of _GadgetSigner_ "Provides dummmy data to satisfy tests and API calls"

BasicGadgetToken.java - dumb (String) implementation of _GadgetToken_

BasicRemoteContentFetcher.java - server-side remoting proxy

BidiSubstituter.java implements GadgetFeatureFactory - Bidirectional language support (i18n). Performs "hangman" substitutions (__MSG_foo__). Builds up a _Substitutions_ and executes it.

<strong>Gadget.java</strong> - It's a gadget! This object is created from a _GadgetSpec_ and ultimately serialised to a string representing the HTML/JS/etc content that sits on the page. Prior to serialisation, the object is subject to a set of transformations, one for each _GadgetFeature_ it requires.

GadgetBlacklist.java interface -  [part of GadgetServerConfig] persists blacklist and lets you query if a given URL is blacklist

GadgetContentFilter.java interface - String->String filter interface to transform the HTML/JS/etc widget content for the browser, e.g. for Caja sanitisation

GadgetContext.java -  This object is passed to each GadgetFeature in the processing sequence to tell it what's going on and help modify its behaviour, since it contains info about gadget server options - ProcessingOptions - as well as Locale, RenderingContext and ServerConfig.

GadgetDataCache.java - [part of GadgetServerConfig] Cache interface. Simply a map from string ID -> Type T.

GadgetException.java - Exception base class

<strong>GadgetFeature.java</strong> - Transforms a _Gadget_ so it will implement a particular feature. prepare() on initial call and void process(Gadget) later on. TODO more

GadgetFeatureFactory.java - Simply an interface to create Gadgets "GadgetFeature create()"

GadgetFeatureRegistry.java - [part of GadgetServerConfig] A map of gadget features in this gadget server. Essentially Gadget ID string -> {feature object, other features it depends on}

<strong>GadgetServer.java</strong>

* Includes processGadget(), which is called by gadget servlet. GadgetID [ie gadget URL] -> _Gadget_ object ready for rendering
* processGadget() adds a sequence of task objects (commands) and executes them:<br/>
 * CacheLoadTask - load gadget from cache instead of fetching/constructing it<br/>
 * SpecLoadTask - load gadget from remote URL (using low-level class, RemoteContentFetcher)<br/>
 * EnqueueFeaturesTask - popalate Gadget's list of required gadget feature objects
* Uses a workflow process:
  Works iteratively - each cycle, it works out which tasks need to be performed. Keeps iterating until all tasks completed or no new tasks can be added. Meanwhile, accumulates all gadget exceptions for *all* iterations so they can be bundled together in a big exception option that's thrown if any exceptions occurred. [Note: I'm not sure why this complicated workflow algorithm is required, when afaict only 3 task objects are present. Maybe more will be added later on.]

GadgetServerConfig.java Configuration options for the gadget server. Composed of java.util.concurrent.Executor, _FeatureRegistry_, _GadgetDataCache_, _MessageBundleCache_, _RemoteContentFetcher_, _GadgetBlacklist_, _SyndicatorConfig_

GadgetServerConfigReader.java Nothing much right now. You'd think it parses a config file or something, but it just ~replicates GadgetServerConfig

GadgetSigner.java interface - defines interface for mapping token ID string -> _GadgetToken_

<strong>GadgetSpec.java</strong> - Dumb data structure encapsulating the spec (xml) ie user prefs, required features, gadget URI, HTML content data, random info-garbles (author etc.)

GadgetSpecParser.java - String xml -> GadgetSpec.
[java]
      GadgetSpecParser specParser = new GadgetSpecParser();
      GadgetSpec spec = specParser.parse(gadgetId, xml.getResponseAsString());
      wc.gadget = new Gadget(gadgetId, spec, prefs);
      (ie xml file becomes spec, spec becomes gadget)
[/java]

GadgetToken.java - Effectively a token string, with a method to sign URLs

GadgetView.java interface - An immutable view of the gadget

JsFeatureLoader.java - Goes into a directory and recursively finds all files matching "feature.xml" Reads each file into a _GadgetFeatureRegistry.Entry_ and registers it into registry (e.g.  feature.containerJs.add(_JsLibrary_) (remember a _GadgetFeature_ modifies the gadget in some way. In the case of a JsFeature (defined in JsLibraryFeatureFactory), the modification is simply to add some JS libraries)

JsLibrary.java [jsLibraries is part of Gadget] - Represents a JS library - holds its source u.g. URL/file)  and capable of reading it to get a string of the JS. The source may be a string representing the JS itself, which is useful if the client simply wants to construct the script text programatically.

JsLibraryFeatureFactory.java implements GadgetFeatureFactory - Provides _GadgetFeatures_ in the case where the gadget feature is simply a JS file (or a list of container JS files and a list of gadget JS files). In this case, the feature's process() method is simply to add all the libraries to the gadget (gadget.addJsLibrary). JsFeatureLoader uses this after trawling through to find the feature.xml for each gadget, since that file simply identifies a bunch of JS libraries.

MessageBundle.java [part of GadgetServerConfig] String ID -> Message map.

MessageBundleParser.java XML file -> _MessageBundle_

MessageBundleSubstituter.java implements _GadgetFeatureFactory_ - Provides _MessageBundleSubstituterFeature_.  This feature is a Javascript library that "compiles" the MessageBundle to Javascript, for a particular locale. It sets up language and country preference (<tt>String setLangFmt = "gadgets.prefs_.setLanguage(%d, "%s");"; String setCountryFmt = "gadgets.prefs_.setCountry(%d, "%s");";</tt>), and then sets up, for each message, the JS mapping from ID -> Message ( <tt>String setMsgFmt = "gadgets.prefs_.setMsg(%d, %s);"</tt> );

ModuleSubstituter.java - Includes _ModuleSubstituterFeature_ which simply replaces __MODULE__ hangman string with the module ID.

OpenSocialFeatureFactory.java - Provides _OpenSocialFeature_

ProcessingOptions.java - Tweaks GadgetServer.processGadget algorithm (methinks this seems like a weird pattern - should instead be attributes of GadgetServer).

RemoteContent.java - Encapsulates results of HTTP call - the content as well as status code, size, etc.

RemoteContentFetcher.java [part of GadgetServerConfig] - HTTP client to grab gadget spec (nb IMO too much BDUF abstraction going on here)

RemoteContentRequest.java - Encapsulates request for HTTP call - headers etc.

RenderingContext.java - enum { GADGET | CONTAINER }

SpecParserException.java - boring exception class

Substitutions.java [part of Gadget] - A collection of Substitutions - each Gadget has a Substitutions object, which it uses for get() queries, e.g. "public String getTitle() { return substitutions.substitute(baseSpec.getTitle()); }".
* Several substitution types MSG BIDI UP(user-prefs) MODULE
* A map for each substitution type, mapping substitution key -> substitution string
* Runs the sequence of substitutions on a given string

SyndicatorConfig.java [part of GadgetServerConfig] Unclear - related to OpenSocial and JSON.

UserPrefSubstituter.java [part of Gadget] - Builds up JSON object with preference values, using Substitutions to perform any substitutions (???)

UserPrefs.java - preference ID -> string (value of preference)

