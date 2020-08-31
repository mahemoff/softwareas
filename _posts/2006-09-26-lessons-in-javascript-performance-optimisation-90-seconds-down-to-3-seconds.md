---
id: 347
title: 'Lessons in Javascript Performance Optimisation: 90 seconds down to 3 seconds'
date: 2006-09-26T23:04:01+00:00
author: admin
layout: post
guid: http://www.softwareas.com/lessons-in-javascript-performance-optimisation-90-seconds-down-to-3-seconds
permalink: /lessons-in-javascript-performance-optimisation-90-seconds-down-to-3-seconds/
dsq_thread_id:
  - "375470785"
categories:
  - Links
  - SoftwareDev
tags:
  - DHTML
  - ERb
  - Javascript
  - Links
  - Optimisation
  - Optimization
  - Performance
  - Rails
  - Tuning
---
<div style="background-color: #fbb; padding:1em; border: #e99 1px solid;">
Summary: Avoid $$(".classname") on large DOMs!!!
</div>

I've recently been optimising the guts out of a JS webapp I wrote, which was making IE crawl to a halt. I discovered this after introducing a stress-inducing data set. (Using Rails' fixtures makes light work of this; since the fixtures are Ruby templates just like the web templates, it's easy to introduce a loop to create lots of data.)

With a rather large data set (100+ items, each several fields), IE would take about 90 seconds to churn through the initial script before the user could do anything. Firefox would run the same thing in about 8 seconds, still too long for a web page, but incredibly about ten times as fast as IE. I'm wanting to avoid pagination at this stage, so first priority was to tweak performance and see if we can keep everything on the same page.

After some sophisticated profiling (<tt>(new Date()).getTime()</tt>:D), the main culprit was  revealed to be prototype's $$. It's a fantastic function, but if you try to grab all elements belonging to a certain class, and the DOM is really big, $$(".cssClassName") can be slow. *REALLY SLOW* in IE. Remedy:

* Removed trivial usages of $$() - e.g. in one case, the script was using it as a simple shorthand for a couple of DOM elements, and it was easy enough to hardcode the array. i.e.
<tt>$$(".instruction")</tt> becomes [$("initialInstruction"), $("finalInstruction")]. The former notation is cuter, but unfortunately impractical on a large web page.
* Introduced <a href="http://www.sylvainzimmer.com/index.php/archives/2006/06/25/speeding-up-prototypes-selector/">the unofficial selector addon</a>. Seems to have improved performance in more complex  queries, i.e. $("#knownId .message"), but doesn't seem to have affected performance of $$(".classname").
* Finally, I bit the bullet and scrapped $$(".classname") altogether. It's more work, but the script now maintains the list of elements manually. Whenever an element is added or removed, the array must be adjusted. Furthermore, even the initialisation avoids using $$(), thanks to some server-side generated JS that explicitly declares the initial list of elements belonging to the class (i.e. the list that would normally be returned by <tt>$$()</tt>). To do this, the following function is called from onload(), generated with RHTML.

[javascript]
function findAllItems() {
<% js_array = @items.map { |item| "document.getElementById('item#{item.id}'),"}.join
      js_array = js_array[0..-2] if @items.length>0 # Drop extra comma at end -%>
      return [<%= js_array %>];
}
[/javascript]

The last step explicitly identifies all items in the class, removing the need to discover them by traversing the DOM. I wasn't really sure how much time it would save - after all, you still have to look the elements up in the DOM and assign them to the array. But when I tried it, the savings were supreme - on IE, from around 45 seconds to about 2 seconds.

I have also incorporated Dean Edwards' superb <a href="http://dean.edwards.name/weblog/2006/06/again/#comment5338">onload replacement</a> to get the ball rolling before images are loaded. It's a neat trick and takes 5 minutes to refactor it in.<!--a75004f7faac0beac68dc5ca0a19c945-->