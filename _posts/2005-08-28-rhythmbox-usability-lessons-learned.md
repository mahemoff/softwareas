---
id: 187
title: 'Rhythmbox &#8211; Usability Lessons Learned'
date: 2005-08-28T15:50:12+00:00
author: admin
layout: post
guid: http://www.softwareas.com/rhythmbox-usability-lessons-learned
permalink: /rhythmbox-usability-lessons-learned/
dsq_thread_id:
  - "375487281"
  - "375487281"
categories:
  - HumansAndTech
tags:
  - Gnome
  - Linux
  - Rhythmbox
  - Software
  - Usability
---
Currently trying to delete about 50 playlists on Rhythmbox. (Rhythmbox doesn't yet have podcast-friendly features like sorting by date, so I end up creating a daily playlist via a bashpodder hack, leading to numerous playlists).

The program's nice overall, but deleting the playlists is a bit slow. I'm manually navigating to each item, right-clicking to open the menu, clicking delete, and confirming. Lessons learned here:

* **Keyboard shortcuts** are good. Like "Del" for delete.
* **Multiple selection** is good. Even for things you didn't think anyone would need to do in bulk. You can't anticipate everything users will do, so as a general rule of thumb ... assume that if a user can do something to *one* thing, they will probably want to do it to *many* things.
* **Expose the configuration files** so I can work out where all this stuff is stored, and manually delete them on the command line. I wish more Linux GUI apps would make it more obvious how the config maps to the filesystem - knowing that should be one of the main benefits of working in Linux.