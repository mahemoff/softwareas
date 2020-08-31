---
id: 137
title: Ajax Live Search Demo
date: 2005-05-30T12:32:30+00:00
author: admin
layout: post
guid: http://www.softwareas.com/live-search-demo
permalink: /live-search-demo/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375383226"
  - "375383226"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
---
<a href="http://www.ajaxpatterns.org/demo/liveSearch/"><img src="http://img261.echo.cx/img261/199/ajaxlivesearch3gk.jpg" style="border: 1pt solid; width: 100%;"/></a>

Over on Ajaxian, there were some [interesting comments](http://www.ajaxian.com/archives/2005/05/ajaxifying_the.html) following from the ["Ajaxifying the Address Bar"](http://www.softwareas.com/ajaxifying-the-address-bar-interface) entry here last week.   I made a little **live search demo to show the kind of idea I had in mind. Please try the [Live Search Demo](http://www.ajaxpatterns.org/demo/liveSearch/) for yourself and let me know how you find it**.

The FAQ is over there, but for all the RSS readers, here's a copy as it stands right now. Jump to the second half for the programming details.

<h2>Using the Live Search</h2>

<h3>How Do I Highlight the Icons?</h3>

<p>It's all demo stuff, everything gets processed by the server, but no actual
lookups going on. So some crude rules apply here ...

</p><dl>
  <dt><b>Web</b></dt><dd>Anything matches.
  </dd><dt><b>Phone</b></dt><dd>Type something resembling a phone number. (e.g. 555-1212) 
  </dd><dt><b>People</b></dt><dd>Type an email address or a Simpsons family name.
  </dd><dt><b>Calculator</b></dt><dd>Type a basic calculator (e.g. 10/5)
  </dd><dt><b>News</b></dt><dd>Include a newsworthy term, e.g. "scandal" or "talks".
</dd></dl>

<h3>Huh? It's Supposed to be a Search Demo - How About, Oh I dunno, RESULTS??!!</h3>

<p>There are no answers here, only questions.

</p><h3>It Doesn't Work on My Browser</h3>

<p>I'm interested in your compatability dillema. If you've got Javascript
enabled and it's not working, please <a href="mailto:michael@mahemoff.com">tell
  me</a> what browser you're using.

</p><h3>Oh, So It's All Pretty Lame, Huh?</h3>

<p>Yeah, lame. The main point here is that all the terms are sent to the
server, which decides on the categories. You could imagine it providing other
info too, like an estimate of the result quantity. Or the results themselves.

</p><p>Do you have any suggestions for a way to make the demo more realistic?
Please <a href="mailto:michael@mahemoff.com">send pointers</a> to any
interesting data repositories which could be held entirely in a memory cache of
a few megs. Or any categories which could be calculated algorithmically.


</p><h2>Background</h2>

<h3>What's This Live Search About?</h3>

A demo of <a href="http://www.softwareas.com/ajax-podcast">AJAX</a> - a
new term for a relatively new way to make the web more dynamic. Written by <a href="http://softwareas.com">Michael Mahemoff</a>. Please mail any comments to
<a href="mailto:michael@mahemoff.com">michael@mahemoff.com</a>.

<h3>Why do you call "Live Search" a pattern?</h3>

It's a neat way to resolve the conflicting forces of user information needs and
bandwidth limitations. In one form or another, several people have discovered
this idea, so I'm capturing it as one of <a href="http://ajaxpatterns.org">the Ajax patterns</a>.

<h3>Whatever. Bodacious Icons, Dude!</h3>

If only I made them myself. They're actually the Crystal Icons for KDE,
released by <a href="http://www.everaldo.com/crystal.html">Everaldo</a> under
LGPL license. Downloaded from <a href="http://linuxcult.com/">LinuxCult</a>.

<h2>Underlying Technology</h2>

<h3>How Does It Work?</h3>

You're perhaps looking for some Ajax tricks. Most of it is apparent by viewing
the source. I'll highlight some of the take-home messages.

<h4>Calling the Server</h4>

Calls to the server are made by ajax.js, which offers a facade to the
XMLHttpRequest object. so you can do this:
      
    callServer(url, 'drawInitialCategories',
                          true, true, null, postvars);

... Which calls the given URL and sends the response to
the drawInitialCategories() callback method. The options specify plain-text
response (not XML), GET request (not POST), and null calling context
object to be passed back to the callback method. Postvars is an array of
variables passed as part of the request.

The library builds on some ideas posted by
<a href="http://smokey.rhs.com/web/blog/PowerOfTheSchwartz.nsf/d6plinks/RSCZ-6CDPEX">Richard
Schwartz</a>. And, more specifically, code posted in a comment there by
<a href="http://www.johnwehr.com/">John Wehr</a>. John's just started <a href="http://ajaxkit.com">AjaxKit</a> and I've been talking to him
about contributing.

The library is seriously untested, so right now, use (if at all) with
caution. The main benefit is thread safety. Compared to the standard
pattern, which uses a global XMLHttpRequest, a new one is created each
time. It's also destroyed after the response returns.


<h4>Setting Up the Images</h4>

The categories are downloaded using a query to the server upon load.
To keep things simple, image names are based on categories. Each image is
then added to a fragment, and the whole thing is added to a div on the
page in one final operation.
      categoriesFragment = document.createDocumentFragment();
      for (i=0; i&lt;allCategoryNames.length; i++) {
        categoryName = allCategoryNames[i];
        var categoryImg = document.createElement("img");
        categoryImg.id = categoryName + "Category";
        categoryImg.src = "http://localhost/ajax/liveSearch/images/"+categoryName+".gif";
        categoryImg.style.backgroundColor="#cccccc";
        categoryImg.title = categoryName;
        categoriesFragment.appendChild(categoryImg);
      }
      document.getElementById("categories").appendChild(categoriesFragment);

<h4>Acting On Input</h4>

Like "Google Suggest", the search uses <a href="http://www.ajaxpatterns.org/SubmissionThrottling">Submission
Throttling</a>. That is, don't query upon each keypress. Instead, every 50
milliseconds, it checks the server *if* the query has changed. This is
achieved with a setTimeout() at the end of the request method, which calls
itself. A BASIC equivalent would be "10 Do something; Sleep; GOTO 10".

      function requestValidCategories() {
        ...
        ...(Call the server if the query has changed)...
        ...
        setTimeout('requestValidCategories();',50);
      }

<h4>Acting On Responses</h4>

The mechanism above shoots off a query to the server whenever the query
has recently changed. It's an <i>asynchronous</i> query, so the response
will be sent to a callback method. In this case,
<i>updateValidCategories</i>. UpdateValidCategories walks through each
category and decides if it's currently valid. Based on its validity, it
updates the background colour, cursor, and onclick action. Note that the
images are transparent, so it's easy to turn them on and off by flicking
the background colour.

        if (validCategoryNames[categoryName]) {
          categoryImg.style.backgroundColor="yellow";
          categoryImg.style.cursor="pointer";
          categoryImg.title = "Category '" +
               categoryName + "'" + " probably has results";
          if (categoryImg.setAttribute) {
            categoryImg.setAttribute("onclick",
                "onCategoryClicked('" + categoryName + "')");
          }
          ...
        } else {
          ...
          ... (turn it off) ...
          ...
        }