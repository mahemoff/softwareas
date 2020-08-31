---
id: 175
title: 'Ajax Patterns: Widgets broken down'
date: 2005-08-13T00:07:10+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-patterns-widgets-broken-down
permalink: /ajax-patterns-widgets-broken-down/
dsq_thread_id:
  - "389987037"
  - "389987037"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - AjaxPatterns
  - Links
  - Patterns
  - Widgets
---
For a long time, the [Ajax Patterns](http://ajaxpatterns.org) had a big section of widgets, about 15 in all. This week, I've been working on full-text versions and they'll be finished on the weekend. Writing the low-level details helped crystallise some of the relationships for me, and I've been able to break those widgets into three groups, which makes a bit more sense now.

So now the structure is this:

* Content Widgets
* Form Widgets
* Page Architecture, which will be renamed, it sounds too grandiose and overarching at the moment, whereas it's really just more patterns at the same level as above.

Here's what they contain - see the [ajaxpatterns homepage](http://ajaxpatterns.org) for up-to-date info. (Excuse the cut-and-paste job).

<h2> Content Widgets </h2>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Drilldown" title="Drilldown">Drilldown</a> See <a href="http://betfair.com" class='external' rel="nofollow">http://betfair.com</a> sidebar.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Microcontent" title="Microcontent">Microcontent</a> Compose the page of "Microcontent" blocks - small chunks of content that can be edited in-page.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Microlink" title="Microlink">Microlink</a>Provide <a href="http://ajaxpatterns.org/Microlink" title="Microlink">Microlinks</a> that open up new content on the existing page rather than loading a new page.</span><span>
</span></li><li> <span class="full"><a href="http://ajaxpatterns.org/Popup" title="Popup">Popup</a> Support quick tasks and lookups with transient Popups, blocks of content that appear "in front of" the standard content.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Portlet" title="Portlet">Portlet</a> Introduce "Portlets" - isolated blocks of content with independent conversational state.</span>
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="http://ajaxpatterns.org/wiki/index.php?title=Main_Page&amp;action=edit&amp;section=16" title="Main Page"></a>]</div><a name="Form_Widgets"></a><h2> Form Widgets </h2>
<ul><li> <a href="http://ajaxpatterns.org/wiki/index.php?title=Live_Command-Line&amp;action=edit" class="new" title="Live Command-Line">Live Command-Line</a> See <a href="http://www.ajaxian.com/archives/2005/05/ajaxifying_the.html" class='external' title="http://www.ajaxian.com/archives/2005/05/ajaxifying the.html" rel="nofollow">Ajaxifying the Address-Bar Interface</a><span class='urlexpansion'>&nbsp;(<i>http://www.ajaxian.com/archives/2005/05/ajaxifying_the.html</i>)</span>.
</li><li> <a href="http://ajaxpatterns.org/Live_Form" title="Live Form">Live Form</a>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Live_Search" title="Live Search">Live Search</a> As the user refines their search query, continuously show all valid results.</span>
</li><li> <a href="http://ajaxpatterns.org/wiki/index.php?title=Query-Report_Table&amp;action=edit" class="new" title="Query-Report Table">Query-Report Table</a> <a href="http://openrico.org/livegrid.page" class='external' title="http://openrico.org/livegrid.page" rel="nofollow">Open Rico Data Table (also illustrates Never-Ending Page)</a><span class='urlexpansion'>&nbsp;(<i>http://openrico.org/livegrid.page</i>)</span>
</li><li> <a href="http://ajaxpatterns.org/wiki/index.php?title=Rich_Text_Editor&amp;action=edit" class="new" title="Rich Text Editor">Rich Text Editor</a> e.g. <a href="http://wikipedia.com" class='external' title="http://wikipedia.com" rel="nofollow">wikipedia</a><span class='urlexpansion'>&nbsp;(<i>http://wikipedia.com</i>)</span>
</li><li> <a href="http://ajaxpatterns.org/wiki/index.php?title=Slider&amp;action=edit" class="new" title="Slider">Slider</a> <a href="http://mindset.research.yahoo.com/search.php?p=ajax&amp;prssweb=Search+the+Web" class='external' title="http://mindset.research.yahoo.com/search.php?p=ajax&amp;prssweb=Search the Web" rel="nofollow">Yahoo Mindset Results</a><span class='urlexpansion'>&nbsp;(<i>http://mindset.research.yahoo.com/search.php?p=ajax&amp;prssweb=Search+the+Web</i>)</span>.
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Suggestion" title="Suggestion">Suggestion</a> Suggest words or phrases which are likely to complete what the user's typing.</span>
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="http://ajaxpatterns.org/wiki/index.php?title=Main_Page&amp;action=edit&amp;section=17" title="Main Page"></a>]</div><a name="Page_Architecture"></a><h2> Page Architecture </h2>
<ul><li> <span class="full"><a href="http://ajaxpatterns.org/Drag-And-Drop" title="Drag-And-Drop">Drag-And-Drop</a> Provide a drag-and-drop mechanism to let users directly rearrange elements around the page.</span>
</li><li> <span class="full"><a href="http://ajaxpatterns.org/Sprite" title="Sprite">Sprite</a> Augment the display with "sprites": small, flexible, blocks of content.</span>
</li><li> <a href="http://ajaxpatterns.org/wiki/index.php?title=Status_Area&amp;action=edit" class="new" title="Status Area">Status Area</a> Variant: <a href="http://ajaxpatterns.org/wiki/index.php?title=Preview&amp;action=edit" class="new" title="Preview">Preview</a> e.g. <a href="http://www.mirimar.net/mailbrowser/" class='external' title="http://www.mirimar.net/mailbrowser/" rel="nofollow">Mail client</a><span class='urlexpansion'>&nbsp;(<i>http://www.mirimar.net/mailbrowser/</i>)</span> showing message list and messages, Outlook style.
</li><li> <a href="http://ajaxpatterns.org/wiki/index.php?title=Virtual_Workspace&amp;action=edit" class="new" title="Virtual Workspace">Virtual Workspace</a> Browser presents a portal into a larger workspace. e.g. Google Maps. Variant [Never-Ending Page] Page keeps adding results as you scroll further down. <a href="http://openrico.org/yahooSearch.page" class='external' title="http://openrico.org/yahooSearch.page" rel="nofollow">Open Rico Yahoo Example</a><span class='urlexpansion'>&nbsp;(<i>http://openrico.org/yahooSearch.page</i>)</span>. Incorporates[Panning And Zooming: e.g. <a href="http://maps.google.com" class='external' rel="nofollow">http://maps.google.com</a>. See <a href="http://mike.teczno.com/giant/pan/" class='external' rel="nofollow">http://mike.teczno.com/giant/pan/</a>. Related: <a href="http://ajaxpatterns.org/Predictive_Fetch" title="Predictive Fetch">Predictive Fetch</a>, <a href="http://ajaxpatterns.org/Browser-Side_Cache" title="Browser-Side Cache">Browser-Side Cache</a>
</li></ul>
