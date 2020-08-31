---
id: 999
title: Including HTML Files from Other HTML Files, on the File:// System
date: 2010-10-14T22:59:56+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=999
permalink: /including-html-files-from-other-html-files-on-the-file-system/
dsq_thread_id:
  - "375574810"
categories:
  - SoftwareDev
tags:
  - Ajax Patterns
  - Experiment
  - IFrame
  - Javascript
  - Programming
  - TiddlyWiki
---
<a href="http://www.27bslash6.com/trash.html"><img style="width:100%;" src="http://picupper.com/2010/10/14/bear_02.jpg"></a><br/>
<span style="font-style:italic; font-size: 50%; line-height: 1em; width: 50%;">"I wont be sending an officer because your not in any danger at all. You have obviously just put a blanket on a dog while it is sitting in your car and taken a photo. "</span>

I still have a passion for web apps that run on the file system. It's an extremely easy development model and extremely flexible. You can send a file (or set of files) to anyone and be confident they can open the files and run your web app, regardless of their operating system and without imposing on them the requirement of setting up a server. Furthermore, they can stick it on a share drive and BAM, guerilla multi-user system. I've had the habit long before I developed for <a href="http://tiddlywiki.org">TiddlyWiki</a> but my time with TiddlyWiki focused my attention on the benefits and taught me a <a href="http://softwareas.com/spa-hacks">number of Single-Page App (SPA) hacks</a> which most web developers are still oblivious to.

And let the SPA hacks roll on ...

As I start to think about resetting the slideshow framework I've been randomly sniping at <a href="http://softwareas.com/html5-the-platform-apps-have-been-waiting-for">conferences</a>recently, one thing I'd like to do is the idea of a file per Master Slide, containing all of the HTML, JavaScript, and CSS. This is more or less how TiddlyWiki themes work, and a very neat modularisation tactic.

Unfortunately, HTML - bless it - can include JavaScript (<tt>&lt;script src="something.js"&gt;</tt>) and CSS (<tt>&lt;link href="something.css"&gt;</tt> etc), but not HTML (which would look something like <tt>&lt;div src="something.html"&gt;</tt> in my dreams). So what are the options for pulling in one HTML file from another HTML file:

* Server-side includes: We've long had server-side includes. I powered my homepage from this less-than-stellar technique for modularisation around 15 years ago. The problem is none too hard to derive from their name. Server, I don't want one.
* XMLHttpRequest: We could make a XHR call and actually this is possible from file to file. Unfortunately, Google Chrome (and maybe others?) sees each file as belonging to a separate domain, making it impossible, and other browsers may issue a warning or confirmation, making it obtrusive.
* File APIs: Again, we could use the magic of $.twFile to read the other file. But this relies on browser-specific hacks and they have to be degraded to a separate Java applet, which requires a proper Java installation, in the case of Chrome, Safari, Opera, and others. Firefox uses Moz-specific API and IE uses ActiveX, which are good but also incur warnings and may be blocked by firewalls. Still, it's not a bad solution. The extra Java applet is a big downside in TiddlyWiki, because you suddenly need to send around two files instead of one, but here I'm already assuming there's a bundle of files to be sent around.
* Outputting HTML inside JavaScript: Since we can read Javascript, we could just spit out the HTML from JavaScript. The benefit here is it works, and works for the most ancient of browsers. But it would require a lot of string manipulation, which would look minging and be unmaintainable, and I massively value elegant code (or at least, the possibility of it).  Many times I have wished JavaScript supported <a href="http://en.wikipedia.org/wiki/Here_document">Here Docs</a>, but alas, it doesn't :(. The best you get is a long sequence of lines ending in \. Unacceptable. You can also achieve this kind of thing with <a href="http://en.wikipedia.org/wiki/ECMAScript_for_XML">E4X</a>, but that's not widely supported.
* Hiding HTML in JavaScript or CSS: I've considered tricks like embedding the entire HTML inside a JavaScript or CSS comment, but the problem is the same reason we need JSONP; when you source a JS or CSS file, your app feels the effects of it, but your code doesn't get to see the source. I'm still holding a candle for the possibility of some CSS hack, like based on <a href="http://blog.stchur.com/2006/06/21/css-computed-style/">computed style</a>, which would let you trick the browser into thinking the background colour of a button is an entire HTML document or something...which would be worth doing just for the sake of being insanely ace.
* Or. iFrames.

Thinking it through, I decided iFrames are your friend. You embed the file to be included as a (hidden) child iFrame. This can work in a couple of ways.

The parent could read the DOM directly:
[javascript]
    var dom = document.querySelector("iframe").contentWindow.document;
    document.querySelector("#messageCopy").innerHTML = dom.querySelector("#message").innerHTML;
[/javascript]
(The child contains message element, the parent contains messageCopy.)

This works on Firefox, but not Chrome, because Chrome sees each file as belonging on a separate domain (as I said above, wrt XHR). So we need to make a cross-domain call. We could be AWESOME and use the under-loved <a href="http://softwareas.com/cors-scraping-and-microformats">Cross-Origin Resource Sharing (CORS) capability</a> to make cross-domain XHR calls, but in this case, it doesn't work because it involves HTTP headers, and we're doing this with pure files.

The solution, then, is another kind of iFrame technique: Cross-domain iFrames. It's been possible to do <a href="http://softwareas.com/cross-domain-communication-with-iframes">cross-domain iFrame communication</a> for a while, but fortunately, modern browsers provide <a href="http://www.whatwg.org/specs/web-apps/current-work/multipage/comms.html">an explicit "HTML5" API for cross-domain iframe communication</a>. I tested it in Chrome, and it works. On Files. Yay.

Under this paradigm, "index.html" contains:
[html]
<script>
  window.onload = function() {
    window.addEventListener("message", function(e) {
      document.querySelector("#messageCopy").innerHTML = e.data;
    }, false);
   document.querySelector("iframe").contentWindow.postMessage(null, "*");
  };
</script>
<h1>Test parent</h1>
<div id="messageCopy"></div>
<iframe src="included.html"></iframe>
[/html]

while "included.html" contains:

[html]
<script>
  window.addEventListener("message", function(e) {
    e.source.postMessage(document.getElementById("message").innerHTML, "*");
  }, false);
</script>
<div id="message">This is the message</div>
[/html]

Point your spiffy HTML5 browser to index.html and watch in glee as the message gets copied from included to includer. I wasn't sure it would work, because certain other things - like Geolocation and Workers - simply don't work in all browsers against the File:// URI, even though they probably should. (Probably because the browsers keep mappings of permissions to each domain, and these systems assume the domain is served with HTTP(s).)

This technique will also degrade to older browsers using those <a href="<a href="http://softwareas.com/cross-domain-communication-with-iframes">"pre-HTML5 hacks</a>. (As the Romans used to say, <em>Omnis enim API HTML V, aequivalet HTML V pre-furta.</em>.)

So I'm glad this technique works and intend to use it in the future, nicely abstracted with a library function or two.