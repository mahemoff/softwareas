---
id: 305
title: 'Portable Comet? It&#8217;s the IFrame, Stupid!'
date: 2006-06-06T07:05:44+00:00
author: admin
layout: post
guid: http://www.softwareas.com/portable-comet-its-the-iframe-stupid
permalink: /portable-comet-its-the-iframe-stupid/
dsq_thread_id:
  - "375572936"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Comet
  - IE
  - IFrame
  - Javascript
  - Links
  - Push
  - Streaming
  - XMLHttpRequest
---
<h2>Comet Takes to IE Like a Fish Takes to Acid</h2>

<a href="http://softwareas.com/comet-podcast">Comet</a> - or <a href="http://ajaxpatterns.org/HTTP_Streaming">HTTP Streaming</A>, if you will - is a little sensitive when it comes to portability, and I'll give you four guesses which major browser is causing the grief?  Yeah, IE makes it difficult for two reasons: (a) IE's XMLHttpRequest component doesn't tell you anything about the response until the connection has closed - even if you try polling it instead of relying on onReadyStateChange, you'll still get an empty string (<a href="http://ajaxify.com/run/streaming/xmlHttpRequest/">Try it</a>); (B) Okay, switch to plan B and inspect IFrame content - we can't rely on onload, which is only called once at the end, so we *must* poll. But no, polling won't help either, as the IFrame content remains empty until (you guessed it) the connection is closed. (<a href="http://ajaxify.com/run/streaming/xmlHttpRequest/iframe/">Try it</a>).

<h2>We're Going Back, Way Back: Inline Script Tags</h2>

Don't give up on the IFrame so fast ... we're closer than we think. Actually, the solution harkens back to one of the original Push techniques: outputting script tags with inline code (what the HTTP Streaming pattern calls "page streaming"). If you do that in your main document, the code will be executed immediately, and the same is true if you do that inside an IFrame.

I'm talking about a service that outputs stuff like this:

[html]
<script type="text/javascript">
    doSomething();
</script>
[/html]

<h2>So Make the Server Spit Out Inline Script Tags</h2>

The portable solution is this: <b>Have the server continuously output script tags that call a known function in the parent frame</b>. When you set the child IFrame's source to point to this service, it will start evaluating the inline scripts as they pop out of the server. This happens to be one technique people have used for remoting for many years (I think Brent Ashley recently told me he was doing it in ?1999). The twist with Comet is that you *keep* doing it, and don't actually close the connection for a while. (Again, I'm sure some people were doing that for a long time too!).

Is it elegant? No. It means the remote service is suddenly coupled to the client-side of the web app - it has to know something about what's in the parent frame, whereas you'd often like it to be generic and just deliver a response in <a href="http://ajaxpatterns.org/XML_Message">XML</a>, <a href="http://ajaxpatterns.org/JSON_Message">JSON</a> or <a href="http://ajaxpatterns.org/Plain-Text_Message">whatever</a>. Like most things Ajax, we're using a hack because it nonetheless push all the right buttons for our users.

<a href="http://ajaxify.com/run/streaming/xmlHttpRequest/iframe/scriptTags/">Try It. Portable Comet for the Masses</a>

<a href="http://ajaxify.com/run/streaming/xmlHttpRequest/iframe/scriptTags/"><img src="http://img62.imageshack.us/img62/2792/streamingtags2wz.png"/></a>

<h2>Here's Some Code I Prepared Earlier</h2>

In the example above, the remote service outputs script tags in a loop - it's a simple countdown service:
[php]
<?
  for ($i=$_GET["start"]; $i>=0; $i--) {
?>
  <script type="text/javascript">
    window.parent.onNewValue(<?= $i ?>);
  </script>
<?
  }
?>
[/php]

And in the browser's initial Javascript, there's a run-of-the-mill onNewValue() function, it looks something like this.
[javascript]
function onNewValue(i) {
  statusDiv.innerHTML = i; // Paint the new value onto the page
}
[/javascript]

See what I mean about coupling? The server-side service had to know that there's a Javascript function defined in the parent called onNewValue(). At least we've minimised the coupling by using an Observer/Event style indirection approach - evidenced by the simple call to "onNewValue()". It would be worse if it was the script that actually performed application logic directly, repainting the DOM with the new value.

<h2>IFrame is the new XMLHttpRequest</h2>

Whoever put the X in Ajax ought to put an I in Comit. IE's XHR component doesn't provide the response until the connection has closed, and I don't think version 7 changes that. Assuming (graciously) it happens in IE8, you'll need to use IFrame for the next five years if you're doing any Comet work. And of course, you won't need to do that, because libraries will do it for you.

BTW You could argue that IE is doing the right thing by preventing access to the content until the connection is closed. Maybe they are, maybe they aren't. From a pragmatic perspective, though, portable Comet requires Ajax. Alternatively, use IFrame with IE and XmlHttpRequest with the others, though I'm not sure if there's much mileage to be gained from this hybrid strategy.
