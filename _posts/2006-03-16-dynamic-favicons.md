---
id: 281
title: Dynamic Favicons
date: 2006-03-16T02:00:54+00:00
author: admin
layout: post
guid: http://www.softwareas.com/dynamic-favicons
permalink: /dynamic-favicons/
dsq_thread_id:
  - "375278861"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - Attention
  - DHTML
  - Favicon
  - HTML
  - Javascript
  - Links
  - Programming
  - Web
---
<p><b><a href="http://en.wikipedia.org/wiki/Favicon">Favicons</a>  should ideally be easy to manipulate, as easy as manipulating the web page's UI.</b> (Favicons are the little website icons you see in the address bar, browser tabs, etc.) <b>For example, a chat app like Meebo could signal that your buddy's trying to contact you, a mail app like GMail could indicate You Have Mail!</b></p>

<p>I've found surprisingly little info on this - is anyone doing it? Anyway, I've been wanting to play around with this for a while and having recently submitted the final <a href="http://ajaxpatterns.org">book draft</a> (post pending), I finally had some spare time to play with it. <b>Fortunately, it turns out to be perfectly feasible - it seems that Firefox and Opera both use &lt;link&gt; tags to determine favico, and this can be changed dynamically to satisfaction.</b> The only gotcha is that you can't try to be too efficient - if you reuse an existing link object and overwrite its href property, the browsers won't pay any attention. so you simply have to remove the existing link tag and add back a new one with the new icon URL. <b>Unfortunately, IE and Safari don't seem to use the link technique at all - I think they just use the "favicon.ico" file. If you know of a way their icons could be dynamically manipulated, please <a href="mailto:michael@mahemoff.com">mail me</a> or add a comment here.</b></p>

<p><b>So I've created a library, <a href="http://ajaxify.com/run/favicon/favicon.js">favicon.js</a>, that lets you manipulate favicons with a single call - <tt>changeFavicon("theIconUrl.ico");</tt>. You can also set the document title, <tt>changeFavicon("theIconUrl.ico", "Hi Everybody!")</tt>, which just sets <tt>document.title</tt>. There are a couple of demos and a brief FAQ</b>:</p>

<ul>
<li><a href="http://ajaxify.com/run/favicon">Type a letter, see the icon change.</a>
</li><li><a href="http://ajaxify.com/run/favicon/cycle">The icons cycle automatically, using a timer.</a> So you can stick it in a background tab and see how it looks.</li>
<li><a href="http://ajaxify.com/run/favicon/#faq">FAQ</a>
</li></ul>

<a href="http://ajaxify.com/run/favicon"><img src="http://ajaxify.com/images/favicon.png" border="0" width="477" alt="Ajaxify favicon demo" /></a>

<b>Implementation Details.</b> Here's the favicon.js code as it stands, all 32 lines of it :-).
[javascript]
var favicon = {

change: function(iconURL) {
  if (arguments.length==2) {
    document.title = optionalDocTitle;
  }
  this.addLink(iconURL, "icon");
  this.addLink(iconURL, "shortcut icon");
},

addLink: function(iconURL, relValue) {
  var link = document.createElement("link");
  link.type = "image/x-icon";
  link.rel = relValue;
  link.href = iconURL;
  this.removeLinkIfExists(relValue);
  this.docHead.appendChild(link);
},

removeLinkIfExists: function(relValue) {
  var links = this.docHead.getElementsByTagName("link");
  for (var i=0; i&lt;links .length; i++) {
    var link = links[i];
    if (link.type=="image/x-icon" && link.rel==relValue) {
      this.docHead.removeChild(link);
      return; // Assuming only one match at most.
    }
  }
},

docHead:document.getElementsByTagName("head")[0]
}
[/javascript]

<strong>Update (Two Days Later)</strong>
<p><em>Crikey!</em> <a href="http://digg.com/design/Dynamic_Favicons">Dugg</a> and on Delicious Popular. And, well, <a href="http://ajaxian.com/archives/dynamic-favicons">Ajaxian too</a> ;-). Digg is interesting ... The last time I submitted <a href="http://digg.com/technology/Binary_Captcha_Test">my own story to digg</a>, it got precisely two diggs (thanks to the other guy!). This time, I didn't bother. Is there a moral here?</p>
<p><em>New, improved, with animate().</em> Most people get dynamic favicons, but some people have said this whole thing is about animation, about as useful as a blink tag, etc. Okay, that kind of misses the main point, which is about notifying the user while a tab is in the background. The FAQ makes it pretty clear that animated  icons was a kind of afterthought (actually, it only occurred to me after I created the cycling demo - changing according to a timer was simply the easiest way to update a background tab, since there's no chat functionality needed or anything like that). But, you know, when a simple idea like that causes seems so wrong to some people, there's probably wheels in it. And while I did say animated GIFs are possibly more elegant in the FAQ, it since occurred to me that it's a bit of a hassle for the casual developer to make an animated GIF. You also get the benefit of compatibility with Opera (and maybe others?). So I've added an <tt>animate()</tt> method, only 8 more lines in all, that lets you cycle through a sequence of images. I expect to post it over the weekend. Mmm...Eye Candy!</p>