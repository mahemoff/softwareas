---
id: 534
title: SVG and VML in One Chameleon File
date: 2009-05-01T10:01:11+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=531
permalink: /svg-and-vml-in-one-chameleon-file/
dsq_thread_id:
  - "375473901"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Ajax Patterns
  - Chameleon
  - Experiment
  - HTML
  - Javascript
  - JOSH
  - Project
  - Web
---
<img src="http://imagecache2.allposters.com/images/pic/MMPH/263463~Boy-George-Posters.jpg" />

<h3>Why a Chameleon File?</h3>

While most browsers support SVG, IE's <a href="http://www.theregister.co.uk/2008/03/06/ie8_standards_roadmap/">unique brand of interopability</a> does not extend that far; even the latest and greatest, incarnation v. 8 of IE, has no sign of SVG. And so, we citizens of the innernets are left with two vector graphics formats: VML for IE, SVG for standards-compliant browsers, which I will simply refer to as "Firefox" for concreteness.

There are tools like <a href="http://draw.labs.autodesk.com/">Project Draw</a> capable of rendering both SVG and VML, and there are convertors like <a href="http://vitali.web.cs.unibo.it/Progetti/VectorConverter">Vector Convertor</a> as well. You can easily end up in a situation where you have two separate files for the same image. In one's endless quest for a simple life of zen-like existence, this is troublesome. You will have to mail the two files around or host the two files somewhere. And if someone changes one, they probably won't bother changing the other one.

One solution would be to convert to a raster/bitmap file, i.e. GIF or PNG, which will then render fine in IE and standards-compliant browsers as well as many other places too. However, this isn't always the best option: (a) if you want to support further editing, you will need the original vector data; (b) it won't scale as nicely; (c) in some cases, the bitmap size is bigger by orders of magnitude.

So a colleague asked me how one could share this type of data and I got thinking about <a href="http://project.mahemoff.com/josh/">a recent experiment</a>. I need to blog it separately, but the premise is that a single file can be different things to different people. In this case, we did some work yesterday I'll describe here - seeing how <strong>a single file can look like VML to something that works with VML (IE) and look like SVG to something that works with SVG (Firefox et al). In the general case, I call this pattern "Chameleon File" and the particular kind of chameleon described here I call a "Vector Graphics Chameleon File".</strong>

<h3>Demo</h3>

The demo link is below - it shows an ellipse in any browser, using either VML or SVG, whichever is supported:

<a href="http://project.mahemoff.com/vector/ellipse.xhtml">http://project.mahemoff.com/vector/ellipse.xhtml</a>

IE users are better off using <a href="http://project.mahemoff.com/vector/ellipse.html">http://project.mahemoff.com/vector/ellipse.html</a> as it won't launch automatically in IE as Windows doesn't recognise the xhtml extension, though it will still launch once you tell windows to open it with IE. The content is the same, the URL is different. I'll explain more below in "Limitations".

(The example is taken from <a href="http://en.wikipedia.org/wiki/Vml">Wikipedia's VML page</a>.)

<h3>How?</h3>

How does it work? Let's look at the source:

[html]
<html xmlns:v="VML">
<!--[if IE]>
 <style>v:*{behavior:url(#default#VML);position:absolute}</style>
<![endif]-->
<body>
 <v:oval style="left:0;top:0;width:100;height:50" fillcolor="blue" stroked="f"/>
  <svg xmlns="http://www.w3.org/2000/svg" width="100" height="50">
    <ellipse cx="50" cy="25" rx="50" ry="25" fill="blue" stroke="none" />
  </svg>
</body>
</html>
[/html]

From Firefox's perspective, the file is valid XHTML thanks to the .xhtml suffix, meaning that the svg tag is fair game. We use the old "if IE" comment trick to get Firefox to ignore the style rule; otherwise it will still work, but it will render the style tag's content (this is XML, not HTML, which would have it un-rendered). It ignores the body and VML v:oval tag, and faithfully renders the SVG. In short, it does what the pure SVG does:

[xml]
<html xmlns:v="VML">
 <style>v:*{behavior:url(#default#VML);position:absolute}</style>
<body>
 <v:oval style="left:0;top:0;width:100;height:50" fillcolor="blue" stroked="f"/>
</body>
</html>
[/xml]

From IE's perspective, this is just a normal VML file with an svg tag snuck in, which thankfully for our purposes, it ignores. So IE sees the file as just regular old VML:

[html]
<?xml version="1.0"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg xmlns="http://www.w3.org/2000/svg" width="100" height="50">
  <ellipse cx="50" cy="25" rx="50" ry="25" fill="blue" stroke="none" />
</svg>
[/html]

<h3>Limitations</h3>

Limitations, I have a couple of those.

<h4>File Extensions</h4>

The extension thing is really annoying (<a href="http://wiki.svg.org/Inline_SVG">see also here</a>). To get SVG working in Firefox, you need Firefox to see the file as XHTML. But to get VML working in IE, IE must see it as HTML. How do you make the browser "see the file" as something? You either set the MIME type in the HTTP header, or you set the file's extension. In this case, we're more interested in the file extension because we want to be able to just mail the file around - in which case there is no MIME type because there's no HTTP header because there's no HTTP because they're viewing it off a file:/// URL - or we want to quickly stick it on a server and not bother faffing with .htaccess-fu and MIME types.

Now that being the case, what file extensions do we need? As far as I can tell, IE must have .html or .htm for the vanilla Windows operating system to open it.

<img src="http://img.skitch.com/20090501-b94j297e7gq3mk87qjpbjkqf1i.jpg" style="width: 380px;" />

As for Firefox, Firefox needs .svg or .xml or .xhtml as far as I can tell.

The problem here is there is no overlap - IE needs .html and .htm, Firefox needs .svg, .xml, .xhtml.

<img src="http://img.skitch.com/20090501-kebkkwx6y8jx6m345h13au56b4.jpg" alt="skitched-20090501-101849.jpg"/>

I spent a while trying to coerce Firefox to see a .html file as XHTML using doctype and the like, but I can't do it - any help here would be appreciated.

The consequence is that you have several possibilities: (a) call it .xhtml/.svg/.xml - it will run on Firefox and IE users will have to "open", "choose application", and set IE (and they can save that setting); (b) call it .html (or .htm but that's just silly) and tell Firefox users to rename the file; (c) distribute two copies of the same file - defeats the purpose of simplicity to some extent, but since it's still the same file, it's not such a big deal; you can keep working with the one file until you're ready to distribute it. Of (a) and (b), I prefer (a) because asking someone to "open with application X" is less onerous than asking someone to rename a file, which sounds a bit odd. On the other hand, in many enterprise situations, you have to optimise around IE users, in which case (b) may well be preferable. You could probably also ship the file with a little instruction to rename the file, targeted at non-IE users using CSS/Javascript hacks, which they will see on opening the file in its HTML guise.

<h4>SVG and VML Feature Sets</h4>

I haven't experimented much with these, but I did find a larger SVG file that didn't work properly. I'm hoping <a href="http://discussion.autodesk.com/forums/thread.jspa?threadID=717036">Project Draw will introduce an easy way to render both SVG and VML for the same file</a>, which would let me script creation of SVG-VML chameleon files for experimentation; or I might just play aronud with a converter. Any data on this would be welcome.

<h3>The Chameleon File Pattern</h3>

... is rather interesting and useful. Some interesting analogies came up in discussion - one of them was the "old woman, young woman" optical illusion. I discovered it's called a "Boring figure" after the experimental psychologist Edwin Boring. I thought "chameleon file" sounded more appropriate than "Boring file"!

<img src="http://picupper.com/2009/05/01/woman.gif" />

Another analogy from <a href="http://whatfettle.org">Paul</a> was the Rosetta Stone - same content in a different format. I think this is a good analogy, but at the same time, I guess the pattern could be used to contain different content too. That's more the case with the JOSH Javascript-HTML Chameleon I'll discuss later on.

<img src="http://picupper.com/2009/05/01/rosettastone.gif" />

It also reminds me of <a href="http://en.wikipedia.org/wiki/Zelig">Zelig</a>, an old Woody Allen flick about a "human chameleon" who tries to be all things to all people, although I think chameleon files have more of their own unique identity.

<img src="http://picupper.com/2009/05/01/zelig.jpg" />

Chamelon File is a hammer, let's go find some nails.

Thanks to <a href="http://jermolene.com">my</a> <a href="http://whatfettle.org">colleagues</a> for <a href="http://www.jonrobson.me.uk">ideas</a> and <a href="http://jaybyjayfresh.com">inspiration</a>.

