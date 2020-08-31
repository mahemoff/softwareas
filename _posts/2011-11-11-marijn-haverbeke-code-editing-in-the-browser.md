---
id: 1449
title: 'Marijn Haverbeke: Code Editing in the Browser'
date: 2011-11-11T12:18:18+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1449
permalink: /marijn-haverbeke-code-editing-in-the-browser/
dsq_thread_id:
  - "468398202"
categories:
  - SoftwareDev
---
Live-blogging Marijn Haverbeke, creator of CodeMirror, at Full Frontal.

Code editors:

* [ACE](http://ace.ajax.org)
* [Orion](http://www.eclipse.org/orion)
* [CodeMirror](http://codemirror.net)

When create [Eloquent JavaScript](http://eloquentjavascript.net), Marijn wanted
to show code cleanly.

ACE - formerly Bespin - was faster and more portable, making CodeMirror look
bad! So CodeMirror 2 is a rewrite based on some of those techniques.

Some performance tricks:
* Indexes both by line number and by vertical offset.
* Only renders the portion of the DOM you can see, plus a little on either side
  in case you scroll just a few lines.
* Selections are passed back to the original text area.

Hijacking browser key events is tricky, browsers don't always let JavaScript
capture events. Chrome has an open bug to let scripts override keyboard.