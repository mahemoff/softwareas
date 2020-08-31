---
id: 414
title: Where Do Widgets Come From? A Look at Widget/Gadget Content Types
date: 2008-02-01T21:07:22+00:00
author: admin
layout: post
guid: http://www.softwareas.com/where-do-widgets-come-from-a-look-at-widgetgadget-content-types
permalink: /where-do-widgets-come-from-a-look-at-widgetgadget-content-types/
dsq_thread_id:
  - "375573461"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Gadgets
  - Google
  - Links
  - Web
  - Web 2.0
  - Widgets
---
<tags>Ajax, AjaxPatterns, Gadgets, Google, Web, Web 2.0, Widgets</tags>

<a href="http://www.ajaxify.com/run/widgets/google/cookies/"><img src="http://img150.imageshack.us/img150/5436/diggrounduploginjl0.png" /></a>

<h3>Background</h3>

A while back, <a href="http://www.softwareas.com/google-gadget-api-for-ajax-developers">I walked through</a> a Google Gadget I made called <a href="http://www.google.com/ig/adde?synd=open&source=ggyp&moduleurl=http://ajaxify.com/run/widgets/google/diggroundup.xml">Digg Roundup</a>, which simply shows Digg headlines and can be customised on topic and popularity. In my quest for an uber-simple tutorial, one thing I skipped on was content type, the subject of the present muttering. There are several content types possible, each with distinct implications for the page architecture and where the gadget sits within it. Below I'll explain the options and help you understand how to decide between them.

A gadget is always expressed as some XML sitting at a URL somewhere on the net. When a developer uploads a gadget to Google, all they do is indicate their server location where the gadget is hosted. So a user's iGoogle homepage is really just a bag of URLs (with layout and preferences for each). Anyways, the gadget is really a mini web page, and inside the gadget XML is a <tt>content</tt> tag that describes the HTML, CSS, and Javascript that makes up this page. The tag has a <tt>type</tt> attribute (i.e. <tt>&lt;content type="xxx"&gt;</tt>) and there are three types available...

<h3>Three Content Types</h3>

<h4><i>html</i> (&lt;content type="html"&gt;)</h4>

<p>All the page content is included in the XML file. It's just like your standard web page HTML; it contains the (initial) HTML body from top to tail (sans enclosing &lt;body&gt; &lt;/body&gt; tags), and CSS and Javascript, which can be inlined or linked, just like a normal web page. The content will be served in an iframe and Google will wrap its own html content around it. In particular, Google will look at other info in your XML file and output html code at the top, such as pulling in libraries and setting up preference data. Incidentally, Google <i>won't</i> add any visual wrap around the widget at this stage; that is the responsibility of the container, which could be iGoogle, Ning, or any standalone web page that chooses to render the gadget.</p>

<p>Although the XML is held on your own server, the iframe will ultimately be served from a Google subdomain as its source. e.g. gmodules.com/blahblah. If you look at iGoogle, you'll see the source is actually something like 50.gmodules.com/blahblah. The point of the "50" is that each gadget on a page comes from a different subdomain, thus isolating gadgets on the same page from each other for security reasons (<a href="http://code.google.com/apis/gadgets/docs/pubsub.html">there are ways around that restriction for consenting gadgets</a>).</p>

<p>The main differences between a &lt;htm&gt; gadget and a normal web page is that your content must be static - the XML file cannot be generated on the fly by your server, because Google will cache it. Think of this kind of gadget as a single file that describes your gadget in isolation, which you could mail around or stick on a USB key. The dynamic behaviour comes from the fact that you can link to external CSS and Javascript (which could be generated on the fly) and, moreover, you will typically be making remote calls once the application is running (either on startup, due to a timer, or in response to system events).</p>

<h4><i>url</i> (&lt;content type="url" href="myserver.example.com/..."&gt;)</h4>
  <p><strong>url.</strong> This could alternatively be called "external" or "hosted". You simply provide a URL on your own web server and deliver up the gadget content from there. Specify "example.com" and the user will see an iframe pointing to "example.com". The content for <i>url</i> gadgets must be dynamically generated, the exact opposite of <strong>html</strong> gadgets, which are always static. This is due to the way these gadgets use </p>

<h4><i>html-inline.</i></h4>

<p>This is <a href="http://groups.google.com/group/Google-Gadgets-API/browse_thread/thread/5776dc1be6dfd0b">no longer supported</a>, but it's worth knowing because (a) the contrasting model helps you understand the other models; (b) older gadgets, as well as Google's own gadgets, are still able to use this model; (c) Google says they <em>might</em> allow special cases through in the future; (d) other containers do support this model (NetVibes anyway). In contrast to the previous types, inlined gadgets are <em>not</em> contained in an iframe; they are served as plain old HTML embedded into the fabric of the page. Just some content in a div.</p>

<h3>A Note on Preferences</h3>

Persistent preferences are a key feature of widgets. Just a quick note that preferences work slightly differently on html vs url widgets (and inline, but I didn't look into it).

With html widgets, the preferences are set as part of the HTML wrap around your widget's HTML. ie some Javascript variables are set up.

With url widgets, the iframe source URL includes some CGI parameters expressing the preferences (e.g. up_storyAmount=5).

Either way, though, Google's preference library abstracts this detail. As long as you declare a dependency on the library, it will be included and will let you access preferences the same way.

<h3>Decisions, Decisions: Which content type to use?</h3>

So that's the definitions. Let's look at the capabilities of each and understand how we might make decisions on which model to use.

<h4>Inline or IFrame (content-type=html/url)?</h4>

Firstly, <strong>inlined (html-inline) versus iframed (html and url)</strong>, assuming inlined is an option for you. Living in the same DOM means that inlined gadgets can talk to each other; dead simple cross-gadget communication is a key benefit of the inlined model. Furthermore, gadgets and the main portal page can talk to each other. You can change the Google logo, for example, or put up a lightbox effect across the entire page.

Not too surprising that raw inlined gadgets were banned; the security risks are high. e.g. An inlined gadget that asks for your gmail credentials would end up storing username and password in global page space, which means a second gadget could simply read that data and upload it somewhere. You could also screw with iGoogle's branding, which Google PR probably didn't appreciate and could lead to phishing attacks. Google could rely on code reviews to minimise the risk of inlined gadgets, but that's a very manual, unscaleable, approach, and users can in fact add gadgets from any URL (although they made it a lot harder to do that a few months ago; AFAICT you need to use the developer gadget in order to add a gadget that's not in the catalogue). Maybe inlined gadgets will come back if a product like <a href="http://code.google.com/p/google-caja/">Caja</a> proves itself worthy of automatically sanitising web apps. It's a hard problem, but there are some good benefits to be had if widgets can live safely together on the same page and domain.

In summary, choose inlined only if you need the extra functionality available and only if you have assessed the risks of tampering from third-party widgets.

<h4>IFrame from widget server (content-type=html) vs IFrame from your own server (content-type=url)</h4>

Second and really the key decision you have to make with Google Gadgets today, <strong>html versus url</strong>. Reason to choose "html" content type over "url" content type:
<ul>
  <li>Javascript API. You can use the full Gadget Javascript API with no effort - you don't even have to include a script tag because iGoogle injects it for you. With the "url" type, using the Gadget Javascript API is a hassle - you have to dynamically generate the script tag, which is not only a bit of scripting effort, but forces you to generate your iframe from a script. Furthermore, cross-domain restriction means that even if you do pull in the API, you can't use the remoting support (the <tt>_IG_Fetch*</tt> functions for proxying and caching).
</li>
  <li>Cross-gadget communication. You can run cross-gadget communication using <a href="http://code.google.com/apis/gadgets/docs/pubsub.html">the Pub-Sub framework</a>.</li>
  <li>Resources. Google serves it for you, which saves bandwidth and maintenance costs. In fact, you will have zero bandwidth costs if your widget functionality is either self-contained (e.g. a calculator) or only hits third-party services (as opposed to your own servers' services).</li>
  <li>Popularity. Pure speculation, but you're probably more likely to be featured in Google's gadget gallery as they can inspect everything about your application's workings (except for any remote calls back to your server).</li>
  <li>Inline-like. If inlined widgets do make a comback, you'll have an easier migration path.</li>
</ul>

Reasons to choose "url" content type over "html" content type:
<ul>
  <li>Full page refreshes. Because it's coming from an external iframe, you can do traditional, non-Ajax, programming. ie. User clicks on link to see a new page. User submits a form. Page auto-refreshes. With this type of widget, you could write a perfectly working gadget without knowing a button of Javascript.</li>
  <li>Personalisation and Security. You can make XHR calls from the widget directly to your own server and make use of any cookies that have been set up. e.g. If the user has already logged into your main web app, then you widgets will be able to present personalised data. With "html" widgets, you would only be able to make use of cookies using cross-domain JSON, and <a href="http://ajaxian.com/archives/joe-walker-on-web-appliaction-security">cross-domain JSON is unsafe</a>. You could possibly do it more safely using the <a href="http://tagneto.blogspot.com/2006/06/cross-domain-frame-communication-with.html">cross-domain iframe fragment identifier hack</a> - <a href="http://wiki.developers.facebook.com/index.php/JavaScript_Client_Library">Facebook's new JS lib</a> works that way - but I haven't investigated it.</li>
  <li>You can easily host the widget as a standalone web page (though it's largely pointless and will look silly unless you pull some CSS madness).</li>
</ul>

<h3>Want to Learn More?</h3>
<ul>
<li><a href="http://ajaxify.com/run/widgets/google/">Digg Roundup</a>. This is the root page for the gadget - there are a bunch of refactorings that try out various features if you click through.</li>
<li><a href="http://code.google.com/apis/gadgets/docs/fundamentals.html">Content types in Google's doco</a>.</li>
</ul>