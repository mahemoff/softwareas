---
id: 141
title: AJAX Frameworks round-Up
date: 2005-06-08T03:48:32+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-frameworks-round-up
permalink: /ajax-frameworks-round-up/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572288"
  - "375572288"
categories:
  - HumansAndTech
  - Links
---
I've been fortunate enough to have received various updates on Ajax projects from some of the developers. Right now, **there are so many new Ajax frameworks coming out, and so much Ajaxification of existing frameworks, that it's getting hard to keep track of what does what. So here's a round-up of Ajax (and related) frameworks, copied from a new page I created on [ajaxpatterns.org](http://ajaxpatterns.org).** I wasn't actually expecting any patterns of frameworks to emerge, but they did ... when you look at all the Ajax-related frameworks out there, you'll tend to notice four distinct styles, as descibed in the background section. I haven't yet looked into the revisited Ajax support on Struts/Tapestry/etc.; those might be quite different.

Please visit [the ajaxpatterns.org frameworks page](http://www.ajaxpatterns.org/AJAXFrameworks) for the latest summary of Ajax frameworks. What follows is a current snapshot which won't be updated.
<hr />
Thanks to everyone who's let me know about the frameworks as they emerge. Please <a href="mailto:michael@mahemoff.com" class='external' title="mailto:michael@mahemoff.com" rel="nofollow">mail Michael Maheomff</a><span class='urlexpansion'>&nbsp;(<i>mailto:michael@mahemoff.com</i>)</span> about any frameworks not yet here, or any corrections. (This is, for now, just a content management system rather than a true wiki.)
<p>As a summary, the <b>pure Javascript frameworks</b> can be divided into two groups:
</p>

<ul><li> <b>Infrastructural frameworks:</b> provide basic piping and portable browser abstractions, leaving the content for the developer to create. Typical functionality:
<ul><li> Wrapper around XMLHttpRequest to encapsulate browser-server interaction. (All frameworks offer this).
</li><li> XML manipulation and interrogation.
</li><li> Performing DOM manipulation according to responses from XMLHttpRequest.
</li></ul>
</li><li> <b>Application frameworks:</b> may offer the above functionality, but are notable for including widget abstractions and other components which are more along the lines of desktop GUI frameworks.
</li></ul>
<p>And the <b>server-side frameworks</b> usually work in one of the following two ways (although they are classified according to language):

</p>
<ul><li> <b>HTML/JS Generation:</b> Server provides complete HTML/Javascript code generation and browser-server co-ordination, so that only browser-side coding is only for customisation.
</li><li> <b>Remote Invocation:</b> Javascript calls routed directly to server-side functions (e.g. Java methods) and returned back to Javascript callback handlers. Or Javascript calls to server to extract information, e.g. session details, database queries.
</li></ul>

<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=1" title="AJAXFrameworks">edit</a>]</div><a name="Pure_Javascript:_Application_Frameworks"></a><h1> Pure Javascript: Application Frameworks </h1>

<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=2" title="AJAXFrameworks">edit</a>]</div><a name="DOJO_.28Under_development.3B_from_September.2C_2004.29"></a><h3> DOJO (Under development; from September, 2004) </h3>
<p><b> <a href="http://dojotoolkit.org/" class='external' title="http://dojotoolkit.org/" rel="nofollow">DOJO</a><span class='urlexpansion'>&nbsp;(<i>http://dojotoolkit.org/</i>)</span> offers comprehensive widget and browser-server messaging support.</b>
</p>
<ul><li> Framework for creation of custom Javascript widgets.

</li><li> Library of pre-built widgets.
</li><li> Browser-server messaging support - XMLHttpRequest and other mechanisms.
</li><li> Support for manipulating URLs in the browser.
</li><li> Open-source license (<a href="http://opensource.org/licenses/afl-2.1.php" class='external' title="http://opensource.org/licenses/afl-2.1.php" rel="nofollow">Academic Free License 2.1</a><span class='urlexpansion'>&nbsp;(<i>http://opensource.org/licenses/afl-2.1.php</i>)</span>). Led by <a href="http://alex.dojotoolkit.org/" class='external' title="http://alex.dojotoolkit.org/" rel="nofollow">Alex Russell</a><span class='urlexpansion'>&nbsp;(<i>http://alex.dojotoolkit.org/</i>)</span> of <a href="http://www.jot.com/" class='external' title="http://www.jot.com/" rel="nofollow">JotSpot</a><span class='urlexpansion'>&nbsp;(<i>http://www.jot.com/</i>)</span>.

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=3" title="AJAXFrameworks">edit</a>]</div><a name="Open_Rico_.28Under_development.3B_from_May.2C_2005.3B_based_on_earlier_proprietary_framework.29"></a><h3> Open Rico (Under development; from May, 2005; based on earlier proprietary framework) </h3>
<p><b><a href="http://openrico.org/demos.page" class='external' title="http://openrico.org/demos.page" rel="nofollow">Open Rico</a><span class='urlexpansion'>&nbsp;(<i>http://openrico.org/demos.page</i>)</span> is a multi-purpose framework with support for Ajax infrastructure and user interaction.</b>
</p>
<ul><li> An XMLHttpRequest response can be routed to one or more callback operation, DOM object, or Javascript object.

</li><li> Easy drag-and-drop.
</li><li> Ajax animation such as scaling and transitions (and presumably the increasingly common idioms such as progress indicators and fading technique?)
</li><li> "Behaviors" - Essentially a widget library.
</li><li>  Open-source. From Sabre Airline Solutions. By <a href="http://looksgoodworkswell.blogspot.com" class='external' title="http://looksgoodworkswell.blogspot.com" rel="nofollow">Bill Scott</a><span class='urlexpansion'>&nbsp;(<i>http://looksgoodworkswell.blogspot.com</i>)</span>, Darren James, and others.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=4" title="AJAXFrameworks">edit</a>]</div><a name="Pure_Javascript:_Infrastructure-Focused"></a><h1> Pure Javascript: Infrastructure-Focused </h1>

<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=5" title="AJAXFrameworks">edit</a>]</div><a name="AjaxJS_.28Raw_alpha.3B_from_May_2005.29"></a><h3> AjaxJS (Raw alpha; from May 2005) </h3>
<p><b><a href="http://ajaxpatterns.org/demo/liveSearch" class='external' title="http://ajaxpatterns.org/demo/liveSearch" rel="nofollow">AjaxJS</a><span class='urlexpansion'>&nbsp;(<i>http://ajaxpatterns.org/demo/liveSearch</i>)</span> is a basic threadsafe wrapper around XMLHttpRequest mainly for Ajax newcomers</b>, still raw alpha and under development, only packaged with the AjaxPatterns live search demo for now. 
</p>
<ul><li> RESTful calls to the server (GET/POST/PUT/DELETE) with plain-text or XML routed to a callback operation.
</li><li> Destruction of used XMLHttpRequest objects.

</li><li> Response caching (planned).
</li><li> Aimed at Ajax newcomers - instead of optimising on performance or footprint, the library will aim to be a readable code base and will provide debugging support.
</li><li> Open-source license. By <a href="http://softwareas.com" class='external' title="http://softwareas.com" rel="nofollow">Michael Mahemoff</a><span class='urlexpansion'>&nbsp;(<i>http://softwareas.com</i>)</span> (with some ideas from John Wehr and  Richard Schwartz).
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=6" title="AJAXFrameworks">edit</a>]</div><a name="HTMLHttpRequest_.28Beta.3B_from_2001.29"></a><h3> HTMLHttpRequest (Beta; from 2001) </h3>

<p><a href="http://www.twinhelix.com/javascript/htmlhttprequest/" class='external' title="http://www.twinhelix.com/javascript/htmlhttprequest/" rel="nofollow">HtmlHttpRequest</a><span class='urlexpansion'>&nbsp;(<i>http://www.twinhelix.com/javascript/htmlhttprequest/</i>)</span> is an alternative to XMLHttpRequest which uses IFrames for superior compatibility.
</p>
<ul><li> Tested and Works: IE6/Win, IE5.5/Win, IE5/Win, IE4/Win, Mozilla/Win, Opera7/Win, Safari/Mac, IE5/Mac.
</li><li> Untested, Probably Works: IE4/Mac, Mozilla/Mac, Opera/Other, Konqueror/Linux. <i>Are you using one of these? The author is requesting compatibility info.</i>
</li><li> Open source license (LGPL). By Angus Turnbull of <a href="http://www.twinhelix.com/" class='external' title="http://www.twinhelix.com/" rel="nofollow">Twin Helix Designs</a><span class='urlexpansion'>&nbsp;(<i>http://www.twinhelix.com/</i>)</span>.

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=7" title="AJAXFrameworks">edit</a>]</div><a name="Interactive_Website_Framework_.28Under_development.3B_from_May_2005.29"></a><h3> Interactive Website Framework (Under development; from May 2005) </h3>
<p><b><a href="http://sourceforge.net/projects/iwf/" class='external' title="http://sourceforge.net/projects/iwf/" rel="nofollow">Interactive Website Framework</a><span class='urlexpansion'>&nbsp;(<i>http://sourceforge.net/projects/iwf/</i>)</span> is a project aiming to support the various aspects of Ajax infrastructure in the browser.</b> Describes itself as a "framework for creating highly interactive websites using javascript, css, xml, and html. Includes a custom xml parser for highly readable javascript. Essentially, all the plumbing for making AJAX-based websites, as well as other common scripts.".
</p>
<ul><li> Thread-safe XMLHttpRequest implementation

</li><li> Wrapper around XML document, so you can make more readable code:
</li></ul>
<pre>   var node = doc.groceries.frozen[0].pizza[0].size;&lt;/pre&gt;
</pre>
<p>instead of manual navigation:
</p>
<pre>   var node = doc.documentElement.firstChild.firstChild.getAttribute("size");&lt;/pre&gt;
</pre>
<ul><li> Open-source license. By <a href="http://circaware.com|Brock" class='external' title="http://circaware.com|Brock" rel="nofollow">Weaver</a><span class='urlexpansion'>&nbsp;(<i>http://circaware.com|Brock</i>)</span>.

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=8" title="AJAXFrameworks">edit</a>]</div><a name="LibXMLHttpRequest_.28Released.3B_June_2003.29"></a><h3> LibXMLHttpRequest (Released; June 2003) </h3>
<p><b><a href="http://www.whitefrost.com/servlet/connector?file=reference/2003/06/17/libXmlRequest.html" class='external' title="http://www.whitefrost.com/servlet/connector?file=reference/2003/06/17/libXmlRequest.html" rel="nofollow">libXmlRequest</a><span class='urlexpansion'>&nbsp;(<i>http://www.whitefrost.com/servlet/connector?file=reference/2003/06/17/libXmlRequest.html</i>)</span> is a thin wrapper around XMLHttpRequest.</b>
</p>
<ul><li> getXML() and postXML() methods.

</li><li> Pooling of XMLHttpRequest objects.
</li><li> Response caching.
</li><li> Source available (obviously), but protected by standard copyright. By <a href="http://www.whitefrost.com/index.jsp" class='external' title="http://www.whitefrost.com/index.jsp" rel="nofollow">Stephen W. Coate</a><span class='urlexpansion'>&nbsp;(<i>http://www.whitefrost.com/index.jsp</i>)</span>.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=9" title="AJAXFrameworks">edit</a>]</div><a name="Sack_.28In_development.3B_from_May_2005.29"></a><h3> Sack (In development; from May 2005) </h3>

<p><b><a href="http://twilightuniverse.com/2005/05/sack-of-ajax/" class='external' title="http://twilightuniverse.com/2005/05/sack-of-ajax/" rel="nofollow">Sack</a><span class='urlexpansion'>&nbsp;(<i>http://twilightuniverse.com/2005/05/sack-of-ajax/</i>)</span> pushes the server response directly into a DOM element.</b>
</p>
<ul><li> Caller specifies the server URL, the data to be sent there, and a DOM element. The DOM element's HTML/content will be replaced with the response.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=10" title="AJAXFrameworks">edit</a>]</div><a name="Sarissa_.28Released.3B_from_February.2C_2003.29"></a><h3> Sarissa (Released; from February, 2003) </h3>

<p><b><a href="http://sarissa.sf.net" class='external' title="http://sarissa.sf.net" rel="nofollow">Sarissa</a><span class='urlexpansion'>&nbsp;(<i>http://sarissa.sf.net</i>)</span> is a Javascript API which encapsulates XML functionality in browser-independent calls.</b>
</p>
<ul><li> Portable XMLHttpRequest creation.
</li><li> Portable XPath queries.
</li><li> Portable DOM manipulation.
</li><li> Portable XSLT.
</li><li> Portable serialisation to XML.

</li><li> Open-source (GPL 2.0 and LGPL 2.1. IANAL and wouldn't have a clue how it can be both at the same time.). From various contributors.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=11" title="AJAXFrameworks">edit</a>]</div><a name="XHConn_.28Released.3B_from_April.2C_2005.29"></a><h3> XHConn (Released; from April, 2005) </h3>
<p><b><a href="http://xkr.us/code/javascript/XHConn/" class='external' title="http://xkr.us/code/javascript/XHConn/" rel="nofollow">XHConn</a><span class='urlexpansion'>&nbsp;(<i>http://xkr.us/code/javascript/XHConn/</i>)</span> is a thin wrapper around XMLHttpRequest.</b>
</p>

<ul><li> Example:
</li></ul>
<pre>
new XHConn().connect(&quot;mypage.php&quot;, &quot;POST&quot;, &quot;foo=bar&amp;baz=qux&quot;, fnWhenDone);
</pre>
<ul><li> Open-source (Creative Commons Attribution-ShareAlike License). By Brad Fults. 
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=12" title="AJAXFrameworks">edit</a>]</div><a name="Server-Side:_Multi-Language"></a><h1> Server-Side: Multi-Language </h1>

<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=13" title="AJAXFrameworks">edit</a>]</div><a name="SAJAX_.28Workable_but_not_1.0.3B_from_early_2005.3F.29"></a><h3> SAJAX (Workable but not 1.0; from early 2005?) </h3>
<p><b><a href="http://www.modernmethod.com/sajax/" class='external' title="http://www.modernmethod.com/sajax/" rel="nofollow">SAJAX</a><span class='urlexpansion'>&nbsp;(<i>http://www.modernmethod.com/sajax/</i>)</span> routes calls directly from Javascript into your server-side language and back out again.</b>
So, for example, calling a javascript method "x_calculateBudget()" will go the server and call a Java calculateBudget() method, then return the value in javascript to x_calculateBudget_cb().
</p>
<ul><li> Faciliates mapping from Javascript stub function to back-end operation.

</li><li> Capable of stubbing calls to numerous server-side platforms: ASP/ColdFusion/Io/Lua/Perl/PHP/Python/Ruby.
</li><li> Open-source license. From various contributors.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=14" title="AJAXFrameworks">edit</a>]</div><a name="JSON_and_JSON-RPC"></a><h3> JSON and JSON-RPC </h3>
<p><b><a href="http://www.crockford.com/JSON/index.html" class='external' title="http://www.crockford.com/JSON/index.html" rel="nofollow">JSON</a><span class='urlexpansion'>&nbsp;(<i>http://www.crockford.com/JSON/index.html</i>)</span> is a "fat-free XML alternative" and <a href="http://www.json-rpc.org/" class='external' title="http://www.json-rpc.org/" rel="nofollow">JSON-RPC</a><span class='urlexpansion'>&nbsp;(<i>http://www.json-rpc.org/</i>)</span> is a remote procedure protocol, akin to XML-RPC, with strong support for Javascript clients.</b>

</p>
<ul><li> <a href="http://www.json-rpc.org/impl.xhtml" class='external' title="http://www.json-rpc.org/impl.xhtml" rel="nofollow">Implementations exist for several server-side platforms</a><span class='urlexpansion'>&nbsp;(<i>http://www.json-rpc.org/impl.xhtml</i>)</span>: Java, Python, Ruby, Perl.
</li><li> Individual packages and licenses for each platform, e.g. <a href="http://oss.metaparadigm.com/jsonrpc/" class='external' title="http://oss.metaparadigm.com/jsonrpc/" rel="nofollow">JSON-RPC-Java</a><span class='urlexpansion'>&nbsp;(<i>http://oss.metaparadigm.com/jsonrpc/</i>)</span>.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=15" title="AJAXFrameworks">edit</a>]</div><a name="Server-Side:_.NET_.28Under_development.3B_from_March_2005.29"></a><h3> Server-Side: .NET (Under development; from March 2005) </h3>

<p><b><a href="http://ajax.schwarz-interactive.de/csharpsample/default.aspx" class='external' title="http://ajax.schwarz-interactive.de/csharpsample/default.aspx" rel="nofollow">Ajax.Net</a><span class='urlexpansion'>&nbsp;(<i>http://ajax.schwarz-interactive.de/csharpsample/default.aspx</i>)</span> is a library enabling various kinds of access from Javascript to server-side .NET.</b>
</p>
<ul><li> Like SAJAX, can pass calls from Javascript into .Net methods and back out to Javascript callbacks.
</li><li> Can access session data from Javascript.
</li><li> Caches results.
</li><li> Free to use, source available, unspecified license. By <a href="http://weblogs.asp.net/mschwarz/" class='external' title="http://weblogs.asp.net/mschwarz/" rel="nofollow">Michael Schwartz</a><span class='urlexpansion'>&nbsp;(<i>http://weblogs.asp.net/mschwarz/</i>)</span>.

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=16" title="AJAXFrameworks">edit</a>]</div><a name="Server-Side:_Java"></a><h1> Server-Side: Java </h1>
<p>Note: Many existing frameworks have recently been adding Java support (e.g. struts), and I will link to those later on.
</p>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=17" title="AJAXFrameworks">edit</a>]</div><a name="Echo_2_.28from_March_2005.29"></a><h3> Echo 2 (from March 2005) </h3>
<p><b><a href="http://www.nextapp.com/products/echo2/" class='external' title="http://www.nextapp.com/products/echo2/" rel="nofollow">Echo 2</a><span class='urlexpansion'>&nbsp;(<i>http://www.nextapp.com/products/echo2/</i>)</span> allows you to code Ajax apps in pure Java (<a href="http://demo.nextapp.com/InteractiveTest/ia" class='external' title="http://demo.nextapp.com/InteractiveTest/ia" rel="nofollow">Demo</a><span class='urlexpansion'>&nbsp;(<i>http://demo.nextapp.com/InteractiveTest/ia</i>)</span>).</b>

</p>
<ul><li> Automatically generates HTML and Javascript.
</li><li> Co-ordinates messages between browser and server. Messaging in XML.
</li><li> Can hand-write custom Javascript components if desired.
</li><li> Open-source license (Mozilla Public License or GNU LGPL). From <a href="http://www.nextapp.com/" class='external' title="http://www.nextapp.com/" rel="nofollow">Next App, Inc.</a><span class='urlexpansion'>&nbsp;(<i>http://www.nextapp.com/</i>)</span>.
</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=18" title="AJAXFrameworks">edit</a>]</div><a name="Direct_Web_Remoting_.28DWR.3B_2005.29"></a><h3> Direct Web Remoting (DWR; 2005)  </h3>

<p><b><a href="http://www.getahead.ltd.uk/dwr/" class='external' title="http://www.getahead.ltd.uk/dwr/" rel="nofollow">Direct Web Remoting</a><span class='urlexpansion'>&nbsp;(<i>http://www.getahead.ltd.uk/dwr/</i>)</span> is a framework for calling Java methods directly from Javascript code.</b>
</p>
<ul><li> Like SAJAX, can pass calls from Javascript into Java methods and back out to Javascript callbacks.
</li><li> Can be used with any web framework - Struts, Tapestry, etc.
</li><li> Follows Spring-like KISS/POJO/orthogonality philosophy.
</li><li> Open-source license (<a href="http://www.apache.org/LICENSE.txt" class='external' title="http://www.apache.org/LICENSE.txt" rel="nofollow">Apache</a><span class='urlexpansion'>&nbsp;(<i>http://www.apache.org/LICENSE.txt</i>)</span>). By <a href="http://www.getahead.ltd.uk/sg/space/joe/" class='external' title="http://www.getahead.ltd.uk/sg/space/joe/" rel="nofollow">Joe Walker</a><span class='urlexpansion'>&nbsp;(<i>http://www.getahead.ltd.uk/sg/space/joe/</i>)</span>. Being incorporated into next <a href="http://www.opensymphony.com/webwork/" class='external' title="http://www.opensymphony.com/webwork/" rel="nofollow">WebWork</a><span class='urlexpansion'>&nbsp;(<i>http://www.opensymphony.com/webwork/</i>)</span> release.

</li></ul>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=19" title="AJAXFrameworks">edit</a>]</div><a name="Server-Side:_PHP"></a><h1> Server-Side: PHP </h1>
<div class="editsection" style="float:right;margin-left:5px;">[<a href="/index.php?title=AJAXFrameworks&amp;action=edit&amp;section=20" title="AJAXFrameworks">edit</a>]</div><a name="AjaxAC_.28From_April.2C_2005.29"></a><h3> AjaxAC (From April, 2005) </h3>
<p><b><a href="http://ajax.zervaas.com.au/" class='external' title="http://ajax.zervaas.com.au/" rel="nofollow">AjaxAC</a><span class='urlexpansion'>&nbsp;(<i>http://ajax.zervaas.com.au/</i>)</span> encapsulates the entire application in a single PHP class.</b> From the website:

</p>
<ul><li> All application code is self-contained in a single class (plus any additional JavaScript libraries)
</li><li> Calling PHP file / HTML page is very clean. All that is required is creating of the application class, then referencing the application JavaScript and attaching any required HTML elements to the application.
</li><li> Built in functionality for easily handling JavaScript events
</li><li> Built in functionality for creating subrequests and handling them
</li><li> Allows for custom configuration values, so certain elements can be set at run time
</li><li> No messy JavaScript code clogging up the calling HTML code - all events are dynamically attached
</li><li> Easy to integrate with templating engine due two above 2 reasons
</li><li> Easy to hook in to existing PHP classes or MySQL database for returning data from subrequests

</li><li> Extensible widget structure to be able to easily create further JavaScript objects (this needs a bit of work though)
</li></ul>
<p>Background:
</p>
<ul><li> Open-source license (Apache 2.0). <a href="http://ajax.zervaas.com.au/" class='external' title="http://ajax.zervaas.com.au/" rel="nofollow">By Zervaas Enterprises</a><span class='urlexpansion'>&nbsp;(<i>http://ajax.zervaas.com.au/</i>)</span>
</li></ul>