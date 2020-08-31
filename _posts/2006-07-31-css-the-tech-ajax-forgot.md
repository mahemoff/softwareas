---
id: 336
title: 'CSS: The Tech Ajax Forgot'
date: 2006-07-31T20:06:40+00:00
author: admin
layout: post
guid: http://www.softwareas.com/css-the-technology-ajax-forgot
permalink: /css-the-tech-ajax-forgot/
dsq_thread_id:
  - "375200146"
categories:
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - CSS
  - HTML
  - Javascript
  - Links
  - Web
  - WebStandards
---
.... Wherein our protaganist awakes to the power of CSS ...

CSS is as important to Ajax as Asynchrony and XMLHttpRequest. Which is to say, it's very useful, even though it's not essential. Due to an accident of the English language, JJG's creative mind, and the propensity of certain terms to rise to buzzdom, it doesn't explicitly feature in "A.J.A.X.". However, <a href="http://adaptivepath.com/publications/essays/archives/000385.php">the original Ajax article</a> certainly spells out the importance of CSS matters - the first of 5 things "Ajax incorporates" is:
<blockquote>
standards-based presentation using XHTML and CSS;
</blockquote>

And in the FAQ below that:
<blockquote>
Why did you feel the need to give this a name?

A. I needed something shorter than â€œAsynchronous JavaScript+CSS+DOM+XMLHttpRequestâ€ to use when discussing this approach with clients.
</blockquote>

Myself, I missed the significance of CSS for a long time. I considered it mostly a useful engineering concept - to cut down on markup - and a way to make things prettier. As I've spent more time creating rich web apps, I've come to appreciate how powerful it is, and how important it is. <b>Not just from a layout perspective, but as a key piece of an overall architecture. With CSS, you can change element visibilty, you can create transparent popups, you can load images faster (using backgroundPosition; see <a href="http://ajaxpatterns.org/Sprite">Sprite pattern</a>).  You can make Flickr-style annotation boxes without a single line of Javascript. You can also support graceful degradation, e.g. keeping an Ajax-related element hidden until the onload script makes it visible (although degrading gracefully for someone not using CSS is another problem altogether). So CSS goes well beyond appearance and even beyond keeping <a href="http://www.artima.com/intv/dry.html">DRY</a>.</b>

Furthermore, scripting with CSS is the best thing since sliced sashimi! At first, I wondered what all the hype was about, but now, I have to say I'd find it hard to go back. I'm using Prototype with the <a href="http://www.sylvainzimmer.com/index.php/archives/2006/06/25/speeding-up-prototypes-selector/">$$  speedup patch</a> and it seems to hold up fine from a performance perspective. It's becoming a standard idiom to loop through each element, using the selector, when the document loads (to do some sort of initialisation).

As one example of selector coolness, here's a library function to clear all input elements, also combining the pleasance of Prototype Rubyish iteration.
[javascript]
function clearInputs(cssSelector) {
  $$(cssSelector + " input").each(function(el) {
     el.disabled = false;
     if (el.type=="text") { ele.value = ""; }
     if (el.type=="checkbox") { el.checked = false; }
  });
  $$(cssSelector + " textarea").each(function(el) { el.disabled = false; el.value = ""; } );
}
[/javascript]

If I want to clear all inputs under submitForm, I call <tt>clearInputs("#submitForm")</tt>. If I want to clear all inputs on the page, I call <tt>clearInputs("body")</tt>. If I want to clear all inputs inside advertising portlets, I call <tt>clearInputs(".portlets .advert")</tt>. Bruce Eckel once said (something like: "It's syntactic sugar, and syntactic sugar is good." He's also spoken about how the average programmer codes X lines per day (canonically ten, but the number doesn't matter). Any syntactic sugar that reduces lines, will probably let you achieve more. Not to say that the number of lines is really fixed, but there's definitely going to be an impact if you're writing a big block instead of a single line. So, yeah, <b>CSS Selectors + Rubyish Iteration, via Prototype, is a big win if you value concise code.</b>

<b>
To sum up, I've found CSS to be a highly valuable skill for modern web development, and for three reasons:
<ol>
<li>The obvious reason that knowing CSS helps make your pages pretty, usable, accessible, etc.
<li>CSS manipulation is important for managing the interaction in rich web apps, including graceful degradation.
<li>CSS Selector Scripting is the new Dependency Injection!
</ol>
</b><!--1dabcd1736ea906bf6fd0ad08f356298-->