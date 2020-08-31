---
id: 348
title: 'Ajax/Javascript: 8 Ways to Create Graphics on the Fly'
date: 2006-10-01T20:37:05+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajaxjavascript-8-ways-to-create-graphics-on-the-fly
permalink: /ajaxjavascript-8-ways-to-create-graphics-on-the-fly/
dsq_thread_id:
  - "375140015"
categories:
  - Links
  - SoftwareDev
tags:
  - Canvas
  - DHTML
  - Images
  - Javascript
  - Links
  - SVG
  - Web
  - Web2.0
  - XBM
---
<iframe style='display:none;' src='http://sandbox.sourcelabs.com/jsondelicious/' width='0' height='0'></iframe><iframe frameborder='0'  scrolling="no" style='width:62px; height:76px; border:0px; overflow:hidden; word-wrap: break-word; float: left; margin: 5px;' src='http://sandbox.sourcelabs.com/diggbutton/?url=http%3A%2F%2Fdigg.com%2Fprogramming%2FAjax_Javascript_8_Ways_to_Create_Graphics_on_the_Fly&title=Ajax%2FJavascript%3A+8+Ways+to+Create+Graphics+on+the+Fly&description=&css='></iframe><noframes><a href='http://digg.com/programming/Ajax_Javascript_8_Ways_to_Create_Graphics_on_the_Fly'>Ajax/Javascript: 8 Ways to Create Graphics on the Fly - digg this</a></noframes>

The ability to create rich graphics on the fly is one of the critical gaps in Ajax. There are indeed techniques to do it, albeit far from perfect, and some are do-able today if you take a pragmatic view of things and keep graceful degradation in mind.

Here I list all the techniques I can think of to create graphics and images dynamically when you're creating an Ajax/DHTML/Javascript web app, with varying degrees of portability and usability. Starting with the obvious and ending with the obscure. Please submit any other techniques you're aware of!!!

<ol>
<li>Use SVG. <a href="http://en.wikipedia.org/wiki/Scalable_Vector_Graphics">Current versions</a> of Firefox, Opera, and Safari (nightly builds) support SVG natively, but with IE and older versions, users need to install a plugin. SVG is an old W3C standard that creates images based on XML. Being a vector format, it stores the image at a high level (curves, lines, etc), so it scales better than a plain bitmap. Here's an SVG circle (adapted from <a href="http://www.w3schools.com/svg/svg_example.asp">W3CSchools</a>:</p>
[xml]
<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">
<circle cx="25" cy="25" r="30" stroke="black"
stroke-width="2" fill="green"/>
</svg>
[/xml]
<p>You could build up the XML string in the code or pull it down from the server with a <a href="http://ajaxpatterns.org/XMLHttpRequest_Call">remote request</a>. However, you don't actually have to specify the XML as a literal string message; you can create a blank SVG document object model (DOM) and manipulate it to build up an image. In this example, we create a circle of radius 25 (adapted from <a href="http://www.kevlindev.com/tutorials/basics/shapes/js_dom/index.htm">this tutorial</a>):
[javascript]
var svgDocument = evt.target.ownerDocument;
var shape = svgDocument.createElementNS(svgns, "circle");
shape.setAttributeNS(null, "cx", 25);
shape.setAttributeNS(null, "cy", 25);
shape.setAttributeNS(null, "r",  20);
shape.setAttributeNS(null, "fill", "green");
[/javascript]
</li>
<li>
<p>Use Canvas. Canvas was introduced in Safari and now in Firefox and Opera too. No sign of life in IE, but this <a href="http://me.eae.net/archive/2005/12/29/canvas-in-ie/">there's a fantastic adaptor hack</a> (<a href="http://ajaxian.com/archives/canvas-in-ie">via Ajaxian</a>) that emulates Canvas using IE's native VML support (more on VML below), and it's now been rolled into an open-source project, <a href="http://excanvas.sourceforge.net/">ExplorerCanvas</a> by <a href="http://glenmurphy.com/blog/2006/03/explorercanvas.html">some Googlers</a>.
</p>
<p>
Where SVG is about <em>things</em>, Canvas is about <em>actions</em>. SVG documents represent images. Canvas tags include code to build up an image, a bit like moving a <a href="http://cse-mjmcl.cse.bris.ac.uk/blog/2006/01/21/1137842060497.html">turtle</a> in the Logo language. So you set a colour, draw something, change the fill style, draw something else, etc. You manipulate a Canvas tag like this:</p>
[javascript]
  var canvas = document.getElementById('tutorial');
  if (canvas.getContext){
    var ctx = canvas.getContext('2d');
    ctx.fillRect(25,25,100,100);
    ctx.clearRect(45,45,60,60);
    ctx.strokeRect(50,50,50,50);
  }
[/javascript]
<p>(BTW Canvas uses the dreaded term, "Context", to refer to what should really be called "paintbrush", "pen", or "turtle" ... more concrete terms than "Context" which imply some sort of metaphor. But wouldn't an imperfect metaphor be easier to grok than the generic "Context"? Alas, it's a common idiom in graphics programming and will be around for a while.)
</p>
</li>
<li>Load dynamic images from the server. Once you have an image tag (either in the initial HTML or created on the fly with document.createElement("img"), you can set its source to any URL, even external to your domain (though cross-domain "hot-linking" should generally be done only with permission). This is standard DHTML/Ajax stuff and works with any browser.
[javascript]
button = document.createElement("img");
button.src = "http://example.com/livechart.gif?interval=15"
[/javascript]
On the server, the image need not be a static image file. It can be a server-side script that happens to output a binary image with the appropriate header, and furthermore, the script can accept CGI parameters, so a unique image can be generated on the fly. Of course, performance will probably suffer if you rely on the server to create images on the fly, and you can only generate them once a second or so. The various Ajax <a href="http://resizr.lord-lance.com/">image manipulation tools</a> do something like this.
</li>
<li>
Use Vector Markup Language (VML). <a href="http://en.wikipedia.org/wiki/Vector_Markup_Language">VML</a> is effectively the MS equivalent of SVG, and as such works in IE, and only in IE. As with SVG, you use XML to specify an image.
[xml]
<v:oval style="position:absolute; left:0; top:0;
               width:100pt; height:50pt" 
               fillcolor="red">
</v:oval>
[/xml]
Fortunately, the Canvas-on-VML hack mentioned earlier means you can take advantage of VML without committing to IE-specific code, though it's (obviously) not a perfect emulation by any means.
</li>
<li>Introduce a <a href="http://ajaxpatterns.org/Richer_Plugin">Richer Plugin</a>, most likely Flash, to beef up the browser's multimedia capabilities.
<li>Rely on plain old CSS and the DOM. You can do some impressive-looking things with just CSS and the DOM, e.g. <a href="http://nubyonrails.com/pages/css_graphs">the CSS graphs library</a>. And of course it's easy enough to make it fully portable too.</li>
<li>Create an image and set its src to a <a href="http://www.mozilla.org/quality/networking/docs/aboutdata.html">data: resource</a>. Firefox and Opera only. From <a href="http://diveintogreasemonkey.org/patterns/add-image.html">Dive Into GM</a>:
[javascript]
var logo = document.createElement('img');
logo.src = 'data:image/gif;base64,R0lGODlhDQAOAJEAANno6wBmZgAAAAAAACH5BAAAAAAA'+    'LAAAAAANAA4AQAIjjI8Iyw3GhACSQecutsFV3nzgNi7SVEbo06lZa66LRib2UQAAOw%3D%3D';
document.body.insertBefore(logo, document.body.firstChild);
[/javascript]
</li>
<li>Embed an XBM file. Yes, some browsers can display XBM images. Works on IE and Firefox, but not Safari or Opera. Unfortunately, XBM has the rather major constraint that it's black-and-white. However, it does have the virtue of being a plain-text format which, like the data: protocol, you can assign an image source to.
<blockquote><p>
If you get your image data in that format in a string (complete with the 
n after each of the #define lines), then you can make any image's SRC 
attribute be:<br/>
"javascript:'"+xbmimagestring+"'"
</blockquote>
<p>XBM's not used often, but there are some nice examples: <a href="http://www.wolf5k.com/faq.html#2">Wolfenstein 5K</a>, most notably, as well as <a href="http://4umi.com/web/javascript/xbm.htm">this bitmap editor</a> and a <a href="http://www.toxi.co.uk/dev/sparklines/">sparklines library</a>.
</li>
</ol>

(Off-topic: I've just updated my blog page, I prefer the 2-column sidebar because: (a) there are now 20 monthly archives links; (b) I wanted to add a ton of chicklets; (c) I wanted to add more bio info. BTW If you have a blog, here's a quick exercise: Place yourself in the mind of a new visitor for twenty seconds, and decide if this person could work out who you are, what you do, and how to contact you. Around 90% of blogs fail this test on the grounds it's impossible or way too hard.)