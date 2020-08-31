---
id: 132
title: Ajaxifying the Address Bar Interface
date: 2005-05-23T19:26:39+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajaxifying-the-address-bar-interface
permalink: /ajaxifying-the-address-bar-interface/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572222"
  - "375572222"
categories:
  - HumansAndTech
  - Links
---
Jeff Attwood asks ["Did you ever get the feeling that the browser address bar is the new command line?"](http://www.codinghorror.com/blog/archives/000296.html) Russel Beattie [expressed a similar sentiment](http://www.russellbeattie.com/notebook/1008310.html) a little while ago:

"(I)t struck me that really what's happening is that the search box is really becoming just the place where we ask our computers questions about anything. It's more than just a search box, it's actually an interface to a rudimentary Artificial Intelligence system."

I like the way google and others do this, but I  think they could do a better job.

**Firstly, they usually don't provide enough variety in the results.They're trying to be intelligent about limiting what I'm asking for, but there's often more than one type of result required.** If I enter ["GOOG"](http://www.google.co.uk/search?q=goog), for instance, I get a nice stock summary and search results for "GOOG". But I'd also like some links to news and groups and so on. If I search on a real word, I'll get a link to Answers.com. That's not such a bad thing, but it would be useful to have direct links to thesaurus, dictionary, wikipedia, et al. Ideal if the resulting page is on answers.com and retains the term, so I can easily switch among the different categories.

**The key is to display lots of results instead of a single result with a blank page, but with differing emphasis.** Yes, it does add some clutter, but it's easy enough to direct the user's eyeballs to the most likely result. If that fails, there's plenty of alternatives already on the page.

Second, there's a need to be more dynamic ... more, shall we say, Ajaxian. Users simply don't know what to search on. You can hide it away in an "About" or "Help" page, or document it in a "Hacks" book, but mainstream users will never look there. With [Live Search](http://www.ajaxpatterns.org/index.php?title=LiveSearch&action=edit) functionality, it should be possible to inform the user about the special-ness of their term. Imagine a UI with a block of icons for concepts like this:

- Search
- News
- Dictionary
- Encyclopedia
- Phone Book
- ...

As the user types, the available options fade in and out to signal whether valid results will be returned. Even without browser-server communication, it would be possible to make a good guess in javascript just against regular expressions.

**Indeed, with AJAX, you can do more than just direct the user's search as they're typing - you can provide results on the fly!** Think google search which keeps updating the hundred results - as well as all quotes and news and all the other stuff - with each keystroke.

**You might be thinking, "gross waste of computational resources, Mahemoff". Maybe, but it's useful to brainstorm design ideas by ignoring most of the technical constraints, and only then pare things back to reality.**

In fact, **I could see live search results being very feasible in what I consider to be the AJAX heartland: intranet applications.** The reward per search on intranets is so much greater than on most public websites, since time wasted can amount to serious loss of productivity. Also, users are less likely to abuse the system. And the result space is much smaller. So I could see live search results being quite feasible in the enterprise.

The other issue here is customisation. **With all the search engines about to go "My"-crazy, it's clear that the results will be able to depend a lot more on the context.** The content and relative emphasis of results will depend largely on the user's context - who's the user, where are they searching from, what's the time, and so on.