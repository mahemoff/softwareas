---
id: 304
title: 'Pseudo-Threading: Multithreading in the Browser'
date: 2006-05-30T22:54:21+00:00
author: admin
layout: post
guid: http://www.softwareas.com/pseudo-threading-multithreading-in-the-browser
permalink: /pseudo-threading-multithreading-in-the-browser/
dsq_thread_id:
  - "375572913"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Javascript
  - Links
  - Multithreading
  - Optimisation
  - Optimization
  - Patterns
  - Performance
  - Threading
  - Web
  - Web2.0
---
<img src="http://img331.imageshack.us/img331/8658/busy6rw.gif"/>

You know <a href="http://ajaxpatterns.org">AjaxPatterns</a>? It's a wiki about Ajax. Anyway, it's now fully open for editing, but I'll post more about that later. Right now, this post covers a particular pattern that's been sitting in eXtreme Stub mode for some time, and has now got a little flesh to it.

<a href="http://ajaxpatterns.org/Pseudo-Multithreading">Pseudo-Multithreading</a> (mmmm...just rolls off the tongue) is a Performance Optimisation pattern to make input smoother. Now that the wiki's open, you could even contribute some info if you've used it.

(The links below don't work as it's a straight HTML copy.)

<hr>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=1" title="Multithreading">edit</a>]</div><a name="Forces"></a><h1> Forces </h1>

<ul><li> Ajax Apps are single-threaded. Browsers don't allow scripts to multithread, and nor does Javascript have any built-in support for it.
</li><li> Most Ajax Apps accept user input.
</li><li> Some Ajax Apps require complex processing in the browser. If the thread of execution is busy performing such processing, users won't be able to perform input.
</li></ul>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=2" title="Multithreading">edit</a>]</div><a name="Solution"></a><h1> Solution </h1>
<p><b>Using <a href="/Scheduling" title="Scheduling">Scheduling</a>, a processing function is called once in a while, incrementally processes a bit more of the problem, before yielding.</b> Instead of solving the entire problem at once and returning, the function maintains a "blackboard" object and continuously works on it until the problem has been solved. This "blackboard" object is optional and may be something that forms the eventual solution, or just a copy of the original problem and an indication of what to do next.

</p><p>For example, imagine you're implementing a <a href="/Portlet" title="Portlet">Portlet</a>, a real estate advertisement providing a mortgage rate calculation. The calculation requires you to run a simulation, calculating the value at the end of each day for a year - a loop of 365 calculations. If you do it all at once, the user won't be able to do anything during that long period. So instead, you break it into chunks of 10 days at a time. At the end of the first chunk, the blackboard indicates the situation after 10 days. At the end of the second chunk, the blackboard indicates the situation after 20 days. At some point, it will reach its target, 365 days, at which point it will probably call a callback function or just handle the result directly, e.g. paint the result on the user-interface.
</p><p>It's convenient to handle this in an object-oriented fashion, where the blackboard data and the processing function belong to the same object. The object is basically a Strategy or Command object (Gamma et al) - it has a "run()" method that does a little bit of processing, and sets values as attributes of itself. In the above example, we have a Calculator object with a run() function that performs the 10-day simulation. calculator.run() begins by reading the daysSoFar attribute, calculator.daysSoFar and the valueSoFar value, calculator.valueSoFar. It then simulates the next 10 days, and updates those attributes. Calculator might also include additional attributes too, such as: the number of days to simulate per run() invocation; the completion condition (which could be a function itself, or just a value such as number of days); a callback function to call upon completion.
</p>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=3" title="Multithreading">edit</a>]</div><a name="Alternatives"></a><h1> Alternatives </h1>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=4" title="Multithreading">edit</a>]</div><a name="Thin_Client"></a><h2> Thin Client </h2>

<p>"Thin Client" Ajax Apps delegate any complex processing to the server. Probably more network and server overhead, but less CPU cycles devoted to processing and more to user input.
</p>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=5" title="Multithreading">edit</a>]</div><a name="Related_Patterns"></a><h1> Related Patterns </h1>
<p>(TODO Patterns like Live Search, Portlet, and Live Form should point here.)
</p>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=6" title="Multithreading">edit</a>]</div><a name="Real-World_Examples"></a><h1> Real-World Examples </h1>
<div class="editsection">[<a href="/wiki/index.php?title=Multithreading&amp;action=edit&amp;section=7" title="Multithreading">edit</a>]</div><a name="NumSum"></a><h2> NumSum </h2> 

<p>The Ajax spreadsheet NumSum, continuously recalculates cell values, using <a href="/wiki/index.php?title=Pseudo-Multithreading&amp;action=edit" class="new" title="Pseudo-Multithreading">Pseudo-Multithreading</a>.
</p>

