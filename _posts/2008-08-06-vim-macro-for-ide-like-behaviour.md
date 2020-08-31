---
id: 468
title: Vim Macro for IDE-Like Behaviour
date: 2008-08-06T08:03:54+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=465
permalink: /vim-macro-for-ide-like-behaviour/
dsq_thread_id:
  - "375573856"
categories:
  - SoftwareDev
tags:
  - Code
  - IDE
  - Javascript
  - Mining
  - Software
  - Vim
---
<img src="http://picupper.com/2008/08/04/vim-editor_logo.png" width="60" height="60">

I find Vim easiest for browsing source and as I explore TiddlyWiki, I decided to use some fairly recent Vim features - vertical splitting and the explorer window. Combined, these give you the feeling you're an 1988 edition of Eclipse. Just like a modern IDE, but navigation is ten times faster.

<img src="http://picupper.com/2008/08/04/Picture%204.png" />

Here's the macro - which assumes you just opened vim or have a single empty buffer:

<b>map ]xx :Explore&lt;cr&gt;2jp&lt;c-w&gt;H20&lt;c-w&gt;&lt;</b>

To switch files, navigate to the new file's name in the explorer window, and hit "p" (the built-in command for "open this file in the <b>p</b>revious location).

The macro:

* Populates the current buffer with an explorer window
* Jumps down two lines (to reach the second filename - the first name is often .svn)
* Opens the file ("p")
* Places the explorer window on the left side (which also forces a re-orientation towards vertically split windows)
* Resizes the explorer window to be 20 columns wide

While in the source window, you can still use commands like ":e filename" to open a new file (with tab completion) and ctrl-o/ctrl-i to jump back and forth.

The other helper is <a href="http://ctags.sourceforge.net/index.html">exuberant ctags</a>, which I installed via Fink. I just run <a href="http://www.vim.org/tips/tip.php?tip_id=94">"ctags *.js"</a> and then I can hyperlink from the file under my cursor using ctrl-], or visit any function using ":tag function-name". (One remaining frustration is I can't get it to hyperlink to OO methods established using the "abc.prototype.xyz = function() {...}" idiom, despite <a href="http://vim-taglist.sourceforge.net/extend.html">including the pattern in ~/.ctags</a>.)