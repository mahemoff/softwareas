---
id: 421
title: Cross-Domain Communication with IFrames
date: 2008-03-31T08:48:29+00:00
author: admin
layout: post
guid: http://softwareas.com/cross-domain-communication-with-iframes
permalink: /cross-domain-communication-with-iframes/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375137396"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Cross-Domain
  - Gadgets
  - IFrame
  - Links
  - Shindig
  - Widgets
---
<h3>An update in the era of HTML5 (May 6, 2011)</h3>

This post has been heavily commented and linked to over the years, and continues to receive a ton of traffic, so I should make it clear that much of this is no longer relevant for modern browsers. On the one hand, they have adjusted and tightened up their security policies, making some of the techniques here no longer relevant. On the other hand, they have introduced technologies that make it easier to do cross-domain communication in the first place.

With modern browsers, you can and should be using <a href="https://developer.mozilla.org/en/DOM/window.postMessage">postMessage</a> for this purpose.

Library support is now available too. All of the following provide an interface to postMessage where it's available, but if it's not, fall back to the primordial techniques described in this article:

* <a href="https://github.com/ternarylabs/porthole/">Porthole</a>
* <a href="http://code.google.com/p/xssinterface/">XSSInterface</a>
* <a href="http://easyxdm.net/">EasyXDM</a>
* <a href="http://benalman.com/projects/jquery-postmessage-plugin/">jQuery PostMessage Plugin</a>

<h3>Now back to the original post ... (from March 31, 2008)</h3>

This article explains iframe-to-iframe communication, when the iframes come from different domains. That you can do this effectively is only now becoming apparent to the community, and is now used in production by Google, Facebook, and others, and has powerful implications for the future of Ajax, mashups, and widgets/gadgets. I've been investigating the technique and working some demos, introduced in the article.

<h2>Background: Cross-Domain Communication</h2>

Ironic that in this world of mashups and Ajax, it's not very easy to do both of them together. Ajax applications run in the browser and such applications were never intended to talk to anything but the server from whence they came. So it's not easy to mash content from multiple sources, when everything must be squeezed through the originating web server. A few hacks have arisen over the years to deal with this, such as <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a>, and the most recent one is a hack involving iframes, which I'll explain in this article. As we'll see later, the iframe technique is arguably more secure than On-Demand Javascript, and it's also better places for communication <em>within</em> the browser, i.e. from one iframe to another.

Related to this article is a <a href="http://www.ajaxify.com/run/crossframe/">demo application</a> and a <a href="http://www.ajaxify.com/run/crossframe/duo">couple</a> of <a href="http://www.ajaxify.com/run/crossframe/framecomms/">variants</a>.

The first mention I've seen of this hack originated on <a href="http://tagneto.blogspot.com/2006/06/cross-domain-frame-communication-with.html">James Burke's Tagneto blog</a> in June, 2006, though I'm fairly certain it's been used in some quarters long before that. It's now used in production by Google in <a href="http://code.google.com/apis/maps/documentation/mapplets/">Mapplets</a>. It's also used in Shindig for widget-container communication. The technique also happens to be the best way to make safe cross-domain calls from the browser directly to a third-party server, which is why it is employed by <a href="http://wiki.developers.facebook.com/index.php/JavaScript_Client_Library">Facebook's new Javascript Client Library.</a>

<h2>The Demo</h2>

First, let's see what we can do with this hack.

<a href="http://www.ajaxify.com/run/crossframe/">Demo</a>

In this demo, we have a control on the top-level document affecting something in the iframe and vice-versa. This shows you can run communication in both directions with this technique. Typical of the technique, the communication is between two browser-side components from different domains (as opposed to browser-to-server communication, although there is actually server communication involved in making this happen).

<h2>The Laws of Physics: What you can do with IFrames</h2>

To understand the hack, we need to understand the "laws of physics" as they apply to iframes and domain policies within the browser. Once you appreciate the constraints in place, the pattern itself becomes trivial. <a href="http://www.ajaxify.com/run/crossframe/framecomms/">This demo</a> was created to explore and illustrate these constraints, and contains some simple code examples.

<strong>Definition I: A "window" refers either to an iframe or the top-level window (i.e. the "main" page).</strong> In our model, then, we have a tree-like hierarchy of windows.

<strong>Law I: Any window in the hierarchy can get a handle to any other window in the hierarchy.</strong> It doesn't matter where they live within the hierarchy or which domain they come from - with the right commands, a window can always refer to any other window. Parent windows are accessed as "parent", "parent.parent", etc., or "top" for the top-level. Child windows are accessed as "window.frames[0]" or "window.frames[name]". Note in this case that the name is <em>not</em> the iframe's <tt>id</tt>, but rather the iframe's <tt>name</tt>. (This reflects the legacy nature of all this stuff, relating back to ugly late-90s frames and framesets.) Thus, to get a sibling handle, you might use "parent.frames[1]".

<strong>Law II: Windows can only access each others' internal state if they belong to the same domain.</strong> This rather puts a kibosh on the whole cross-domain cross-iframe thing. All this would be so easy if iframe scripts could talk to each other directly, but that would cause all manner of security shenanigans. <a href="http://blog.monstuff.com/archives/000304.html">HTML 5 does define explicit communication between iframes</a>, but until wide adoption, we have to think harder ...

<strong>Law III: Any window in the hierarchy can set (but not read) any other window's location/URL, even though (from Law II) browser security policies prevent different-domain iframes from accessing each other's internal state.</strong> <i>Note: Exact details for this law needs further investigation</i> Again, it doesn't matter which domain it comes from or its position in the hierarchy. It can always get a handle on another window and can always set the window's URL, e.g. "parent.frames[1].location.href". This establishes window URLs as the one type of information on the page which is shared across all windows, regardless of the domain they come from. <em>It seems sensible that a parent can change its child windows' URLs, BUT not vice-versa; how strange that a child window is allowed to alter its parent's (or uncle's, sibling's, etc.) URLs! The only justification I know of is the old technique of escaping the frame trap, where a website, upon loading, ensures it's not inside a frame by simply setting the top-level URL - if it's different to itself - to its own URL. This would then cause the page to reload to its own URL. However, that's a special case and hardly seems worth justifying this much leeway. So I don't really know why you can do this, but lucky for us, you can!</em>

<strong>Law IV: When you change the URL's fragment identifier (the bit on the end starting with a #, e.g. http://example.com/blah#fragmentID), the page doesn't reload.</strong> This will already be familiar to you if you're familiar with another Ajax hack, <a href="http://Unique_URLs">Unique URLs</a> to allow for bookmarkability and page history. Normally, changing a document's "href" property causes it to reload, but if you only change the fragment identifier, it doesn't. You can use this knowledge to change the URL symbolically - in a manner which allows a script to inspect it and make use of it - without causing any noticeable change to the page content.

<h2>Exploiting the Laws of Physics for Cross-Domain Fun and Profit - The Cross-Domain Hack (URL Polling version)</h2>

The laws above are all we need to get cross-domain communication happening. The technique is simply this, assuming Window A wants to control Window B:

* Window A changes Window B's fragment identifier.
* Window B is polling the fragment identifier and notices the change, and updates itself according to the fragment identifier.

Ta-da!!! That's the whole thing, in its glorious entirety. Of course, you had to know the laws of physics in order to understand why all this works. It simply relies on the fact that both Window A and Window B have one common piece of state - the URL - and the fact that we can change the URL unintrusively by manipulating only the fragment identifier. For example, in the demo, the iframe's URL changes to <tt>http://ajaxpatterns.org/crossframe/#orange</tt> and once the iframe script notices it, it updates the colour.

A few observations:

* This works in either direction. Parent to child, child to parent. As the demo illustrates.
* It requires co-operation from both parties; it's not some magic way to bypass browser security mechanisms. Once Window A changes Window B's fragment identifier, it's up to Window B to act on the change; and it's up to Window B to be polling the fragment identifier in the first place.
* Polling the fragment identifier happens to be exactly the same technique used in the <a href="http://Unique_URLs">Unique URLs</a> pattern.

There are a couple of downsides: (a) Polling slows down the whole application; (b) Polling always involves some lag time (and there's always a trade-off a and b - the faster the response, the more cycles you application uses up); (c) The URL visibly changes (assuming you want to manipulate the top-level window). We'll now consider a second technique that addresses these (albeit in a way that introduces a different downside).

<h2>The Cross-Domain Hack (Marathon version)</h2>

Here's a variant which no longer involves polling or changing any URLs. I learned of it <a href="http://www.julienlecomte.net/blog/2007/11/31/">from Juliene Le Comte's blog</a>, and he's even packaged it as a library.

Looking back at Law II: "Windows can only access each others' internal state if they belong to the same domain". At the time, I made this sound like a bad thing, but as David Brent likes to say, "So, you know, every cloud ...". The law is bad if you state it as "cross-domain iframes can't play with each others' toys" (paraphrasing the <a href="http://c2.com/cgi/wiki?LawOfDemeter">informal version of Demeter's law</a>). But it's good if you spin it as "well, at least <em>same-domain</em> iframes <em>can</em> play with each others' toys". That's what we're going to exploit here.

As for the demo, the functionality is the same, but since this one involves spawning iframes, I've left them intact, and made them visible, for your viewing delight. Normally, of course, they'd be invisible, and the application would look exactly the same as the previous demo.

<a href="http://www.ajaxify.com/run/crossframe/duo"><img src="http://img101.imageshack.us/img101/8923/crossframemarathonpj9.png" /></a>

Here's how this technique works:

* Every time Window A wants to call Window B, it spawns a child iframe, "Window B2" in the same domain as Window B. The URL includes the command being issued (as a CGI parameter, fragment identifier, or any other URL pattern which will be recognised by the destination script).
* When window B2 starts up, its Javascript inspects the URL, gets a handle on Window B, and updates Window B according to the URL (e.g. a CGI parameter).
* Window B2 destroys itself in a puff of self-gratified logic.

So in this case, we create a new, short-lived, iframe for every message being passed. Because the iframe comes from the same domain as the window we're trying to update, it's allowed to change the window's internal state. It's only useful to us on startup, because after that we can no longer communicate with it (apart from by the previous fragment identifier trick, but we could do that directly on the original window).

Window B2 is sometimes called a proxy because it accepts commands from Window A and passes them to Window B. I like to think of it as Pheidippides of <a href="http://en.wikipedia.org/wiki/Marathon"> fame; it passes on a message and then undergoes a noble expiration. Its whole mission in life is to deliver that one message.

This technique comes with its own downside too. Quite obviously, the downside is that you must create a new iframe for every call, which requires a trip to the server. However, with caching in place, that could be avoided, since everything that must happen will happen inside the browser. So it would simply be the processing expense of creating and deleting an iframe element. Note that the previous variant never changed the DOM structure or invoked the server.

Also, note that in either versions of the hack, there is the awkward matter of having to express the request in string form, since in either pattern, you are required to embed the request on the window URL.  There is <a href="http://www.alexpooley.com/2007/08/07/how-to-cross-domain-javascript/">an inspired extension of this hack</a> that also has some untapped promise in this area. It involves setting up a subdomain and updating its DNS to point to a third-party website. When combined with the old <a href="http://fettig.net/weblog/2005/11/30/xmlhttprequest-subdomain-update">document.domain hack</a>, you end up with a situation where your iframe can communicate with a cross-domain iframe, without relying on iframe. (The technique described in the article is about browser-to-server communication, but I believe this iframe-to-iframe is possible too.)

<h2>A Third Hack Emerges: Window Size Monitoring</h2>

<a href="http://shouldersofgiants.co.uk/Blog/post/2009/08/17/Another-Cross-Domain-iFrame-Communication-Technique.aspx">A  newer third hack by Piers Lawson</a>  is based around the porous nature of window sizes and the use of window.resize(). Fragment IDs are used like in the first technique here, but instead of polling, window resize events are used to cause a more direct trigger.

<h2>Applications</h2>

<h3>Cross-Domain IFrame-to-IFrame Calls ... and Widgets/Gadgets</h3>

In the world of mashups, iframes are a straightforward way to syndicate content from one place to another. The problem, though, is limited interaction between iframes; in pure form, you end up with a few mini web browsers on a single page. It gets better when the iframes can communicate with each other. For example, you can imagine having iGoogle open, with a contacts widget and a map widget. Clicking on a contact, the map widget notices and focuses on the contact's location. This is possible via <a href="http://code.google.com/apis/gadgets/docs/pubsub.html">Gadget-To-Gadget communication</a>, a form of publish-subscribe which works on the iframe hack described here. And speaking of maps, check out <a href="http://code.google.com/apis/maps/documentation/mapplets/basics.html">Google Mapplets</a>, which are a special form of gadget that work on Google Maps, and also rely on this technique.

In terms of gadgets, another application is communication between a gadget and its container, and this is something I've been looking at wrt Shindig. For example, there is a dynamic-height feature gadgets can declare. This gives the gadget developer an API to say "I've updated, now please change my height". Well, an iframe can't change its own height; it must tell its parent to do that. And since the gadget lives in an iframe, on a different domain as the container (e.g. iGoogle), this requires a cross-domain, cross-iframe, message. And so, it uses this technique ("rpc" - remote procedural call - in shindig terminology) to pass a message to the container.

<h3>Cross-Domain Browser-to-Server Calls</h3>

The best known technique for calls from the browser to an third-party server is <a href="On-Demand Javascript">On-Demand Javascript</a>, aka Javascript APIs aka JSON/JSONP. This was obscure in 2005, with Delicious being the best example. Now, it's big time in Web 2.0 API land, and Yahoo! has exposed almost all of its APIs this way, and Google also provides data such as RSS content via JSON.

It works by spawning a new script element programmatically, an element pointing to an external Javascript URL. Since there's no restriction on third-party Javascript running, the browser will faithfully fetch and execute the script, and so the script will typically be written to "return" by updating variable and/or calling an event handler.

There are two major security issues with On-Demand Javascript. Firstly, you have to trust the API provider (e.g. Yahoo!) a lot because you are letting them run a script on your own web page. And there's no way to sanitise it, due to the script tag mechanism involved. If they are malicious or downright stoopid, your users may end up running an evil script which could ask for their password, send their data somewhere, or destroy their data altogether. That's because whatever your web app can do, so can the third party's script, even if you're only trying to get a simple value back. The mechanism forces you to hand over the keys to the Ferrari when all you want is a new bumper sticker. Secondly, what's to stop other websites also making use of the external Javascript? If your own site can embed the script to call a third-party JS API, so too can a malicious fourth-party. This is fine for public, read-only, data, but what if you're relying on the user's cookies to make privileged calls to the third-party? Then the fourth-party's web app will be just as capable of issuing calls from the browser to the third-party, and they might well be more evil calls than you're making, e.g. "transferFunds()" instead of "getBankBalance()". The moral is: Javascript APIs  can only be used for serving public data.

Whoa!!! Public data only? That's a tragic restriction on our cross-domain API! For mashups to be truly useful, it must be personal. We'll increasingly have OAuth-style APIs where users will tell Site X that Site Y is allowed to read its data. But how can that work in the browser? How can Site Y expose its data so that it's usable from the browser, but only when Site X is running? It can't work with On-Demand Javascript. Site Y could try reading the referrer headers to see where the call is coming from, but anyone could write a command-line client with fake headers.

In fact, the answer is to use the iframe hack described in this article. As I mentioned earlier, this is how Facebook gets the job done, with what is essentially the same "power of attorney" delegation model as OAuth (BTW thanks to my colleague <a href="http://osmosoft.com">Jeremy Ruston</a> for the "power of attorney" OAuth analogy - albeit it was stated in a slightly different context from OAuth).

I haven't looked too much into the mechanism involved with the Facebook API, but it looks like it's essentially using a variant of the Marathon technique. From memory, there's an ever-present invisible facebook.com iframe. Each time your web app make a Facebook call, the Facebook JS library spawns a new "proxy" iframe, which passes the message on to its same-domain ever-present frame, which makes a bog-standard XHR call to Facebook. So now we're making an XHR call to another domain, which we can get away with because it's coming from a separate iframe. Once the XHR call returns, I think the message is returned to your application (this happens via another same-domain iframe you must host on your server, though I think that's unnecessary) and the proxy iframe disappears.

Note that all Facebook ever exposes is a standard web service that relies on the user being logged into Facebook - there's no Javascript involved. The user must be logged in and must have given permission for the application to access its Facebook details. Effectively, the user is allowing a particular website URL to make Facebook calls, since the application developer must register the URL. If you look back at the iframe algorithms I described earlier, you'll see that it's straightforward for Facebook to ensure that only this application (and any other application the user trusts) can access the data. The Facebook.com iframe (whose behaviour is controlled by IFrame and can't be tampered) simply has to inspect the URL of the parent window and pass it to the server as part of the XHR call. The server can then check that the logged-in user has authorised this application, using the URL to identify it.

As for the first concern of cross-domain Javascript - having to trust the third-party API provider - I believe the iframe technique overcomes this concern too. Facebook.com never gets to run arbitrary Javascript on your server. Of course, you have to trust the Facebook library and the Facebook-provided iframe you're required to host on your domain, but those could be audited prior to installation. All those things are set up to do is call callback methods inside your top-level application; you could inspect the library and ensure that's all that will ever happen.

Thus, cross-domain iframe-based communication solves both problems which have plagued On-Demand Javascript. It <em>is</em> slightly more complicated, however.

<h3>Conclusions</h3>

Yes, this is a somewhat complicated technique. Actually understanding the problem it solves is really the hard part! Once you understand that, and once you understand those laws of physics, the trick is actually quite straightforward (either version of it).

The technique will be critical for gadget containers such as Shindig. As OAuth takes off, we'll also see the technique used a lot more in mainstream applications and APIs.

With HTML 5, cross-frame messaging will render the hack unnecessary for iframe-to-iframe communication. Indeed, the aforementioned Cross-Domain library uses that technique already for Opera, in a fortuitous twist of fate since Opera doesn't actually support everything this hack requires. However, the notion of using iframes for cross-domain calls will still be  present, no matter how the windows talk to each other.