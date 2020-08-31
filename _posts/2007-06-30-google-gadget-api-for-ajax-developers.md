---
id: 387
title: Google Gadget API for Ajax Developers
date: 2007-06-30T12:55:06+00:00
author: admin
layout: post
guid: http://www.softwareas.com/google-gadget-api-for-ajax-developers
permalink: /google-gadget-api-for-ajax-developers/
dsq_thread_id:
  - "375173250"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Gadget
  - Google
  - Links
  - Widget
---
I just made my first Google Gadget - <a href="http://ajaxify.com/run/widgets/google/">a Digg roundup tool</a>. Here are some quick notes on making a Google Gadget for Ajax developers. I assume you know Ajax and also that you've played around with <a href="http://google.com/ig">iGoogle</a> as a user.

<a href="http://ajaxify.com/run/widgets/google/"><img src="http://ajaxian.com/wp-content/images/diggroundup.png"></a>

<h3>What's a Gadget?</h3>
<ul>
  <li>The gadget is an XML file sitting on your server. In my case, <a href="http://ajaxify.com/run/widgets/google/diggroundup.xml">http://ajaxify.com/run/widgets/google/diggroundup.xml</a>. It will get cached, so effectively it must be a static file.</li>
  <li>The user adds your gadget to their igoogle portal, or codes it into their own website, by specifying this URL (it may be done indirectly - via the gadget registry. You'll appear in the registry if you've submitted your gadget to igoogle.)</li>
  <li>The gadget is rendered as an iframe, so you have all the usual security constraints which stop you borking the portal and other gadgets. This also means you can't communicate with other Gadgets other than via than remote calls to a common third-party server (or has anyone tried hooking them together using <a href="http://tagneto.blogspot.com/2006/06/cross-domain-frame-communication-with.html">the iframe-fragment identifier</a> hack? ).
</ul>

<h3>The Gadget Content</h3>
<ul>
  <li>The XML file contains three main sections: module settings, user preferences, and the iframe content.</li>
  <li>Module settings (&lt;ModulePrefs&gt;) are the usual demographic stuff - module name, your email, blood type, etc. Mostly optional.</li>
  <li>User preferences (&lt;UserPref&gt;) are things users can edit by hitting the Edit button. Note that these aren't dynamic app variables like a user's search query - they are longer-term preferences like background colour and number of results to show. Each time the user changes then, the entire gadget is reloaded, so you can assume in initialisation that the preferences have already been established, and you don't need to bother checking if they're changed. The nice thing about preferences is they're declarative, so you don't have to manage input and persistence. You just say "I need a number called resultAmount from the user" (<tt>&lt;UserPref name="resultAmount" display_name="No. of Results" default_value="5" datatype="string" &gt;&lt;/UserPref&gt;</tt>). Later on, you'll be able to interrogate a prefs object to get back the data.</li>
  <li>The content. The content is pretty much the "body" part of an IFrame. ie. your html and ... you'll never expect this ... the javascript. You probably expected the JS to be in a separate section of the XML file, but you simply include it using an inline script tag (<tt>&lt;script tag="text/javascript"&gt;the script...&lt;/script&gt;</tt>, wherever you fancy. The same goes for CSS - just include a <tt>&lt;style type="text/css"&gt;</tt> section at the start of your script or inline it. So much for unobtrusive Javascript/CSS, but you can and should still separate things out within your page content.</li>
</ul>

<h3>User Prefs example</h3>

This is what the user prefs looks like:

<img src="http://img261.imageshack.us/img261/1238/userprefssk8.png">

It comes from this definition:
[xml]
   <UserPref name="bgColor" display_name="Background Color:" default_value="White" datatype="enum" >
        <EnumValue value="White" />
        <EnumValue value="Pink" />
        <EnumValue value="Aqua" />
        <EnumValue value="Lime" />
        <EnumValue value="Yellow" />Â·
        <EnumValue value="Orange" />
        <EnumValue value="Black" />
    </UserPref>
   <UserPref name="container" display_name="Story Type:" default_value="" datatype="enum" >
        <EnumValue value="" display_value="All" />
        <EnumValue value="technology" display_value="Technology" />
        <EnumValue value="science" display_value="Science" />
        <EnumValue value="world_business" display_value="World Business" />
        <EnumValue value="sports" display_value="Sports" />
        <EnumValue value="entertainment" display_value="Entertainment" />Â·
        <EnumValue value="gaming" display_value="Gaming" />
    </UserPref>
   <UserPref name="storyAmount" display_name="No. of Stories:" default_value="5" datatype="string" >
   </UserPref>
   <UserPref name="popularOnly" display_name="Popular Only?" default_value="true" datatype="bool" >
   </UserPref>
[/xml]

and is accessed like this:

[javascript]
var prefs = new _IG_Prefs(__MODULE_ID__);
message.style.backgroundColor = prefs.getString("bgColor");
[/javascript]

<h3>Remote Content</h3>
<ul>
<li>Your gadget probably takes remote content. Remember it's a static XML file, so you can't output such content on the fly - you have to use <a href="http://ajaxpatterns.org/XMLHttpRequest_Call">some kind of web remoting</a>. Because of cross-domain restrictions, you will want to use a <a href="http://ajaxpatterns.org/Cross-Domain_Proxy">Cross-Domain Proxy</a>. (I experimented with direct <A href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a>, but no cigar.) Fortunately, Google provides a nice API for proxying, which also caches the content you're grabbing. The main call is _IG_FetchContent(url, callbackFunc). The callback function is given the contents of URL. As mentioned in <a href="http://www.softwareas.com/digg-api-cant-bust-the-cache">my previous post</a>, this might cause some problems if you need to refresh the cache more than once an hour.</li>
</ul>

<h3>Development Tips</h3>
<ul>
<li>igoogle can give some pretty poor error messages when you're just starting up. If there's nothing at the URL you specify, you will get a weird XML parsing error rather than a good old 404 warning. I also found if you have certain errors such as a typo in your XML file, igoogle says the gadget doesn't exist at that URL, even though in this case, it does! For those reasons, be sure to start with Google's <a href="http://www.google.com/apis/gadgets/gs.html#Hello_World">Hello World</a> and work from there!</li>
<li>Develop on your server directly. (If the gadget is live, you might make a test copy of it for debugging.) You don't want to be developing on your local box and continuously uploading/checking it in, because igoogle needs to fetch it from a URL each time you want to test it.</li>
<li><strong>The secret sauce is this</strong>: <a href="http://www.google.com/apis/gadgets/tools.html#Dev_Gadget">The Developer Gadget</a>. This is a special gadget provided by igoogle that, if you include it on your portal, will let you suppress caching of your app, which you absolutely have to do. It also makes it a bit easier to add a new gadget and view the gadget source code.</li>
<li>Speaking of gadget source code, you can view the entire gadget XML for any gadget you come across, so take advantage of that and avoid reinventing the wheel.</li>
</ul>

The Developer Gadget looks like this:
<img src="http://img165.imageshack.us/img165/7013/devgadgetyd8.png"><!--802ef684e65726e1dbb86668e8f64ccf-->