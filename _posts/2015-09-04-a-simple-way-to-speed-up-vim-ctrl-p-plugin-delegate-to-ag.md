---
id: 2172
title: 'A simple way to speed up Vim Ctrl-P plugin: Delegate to Ag'
date: 2015-09-04T09:51:38+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2172
permalink: /a-simple-way-to-speed-up-vim-ctrl-p-plugin-delegate-to-ag/
categories:
  - Uncategorized
---
[Ctrl-p](https://github.com/kien/ctrlp.vim) is "Intellisense for Vim", allowing you to quickly jump to a file by searching for a few letters or even fancy camel-case type searches. (e.g. find article_editor.rb by searching for "ae").

However, doing all this requires it to maintain a search index, aka cache, to be maintained. That can be very frustrating with a big project as it takes 5-10 seconds to update, which is not a good thing when you're desperately trying to jump around files. This delay would be fine if Ctrl-P worked in the background, but due to Vim limitations, it can't, so you have to frequently run it on the command-line and wait for the update.

Or do you?

No you don't. Here is a trick that lets you **never wait for ctrl-p again**! Just add this to your vimrc:

<pre>
let g:ctrlp_user_command = 'ag %s -i --nocolor --nogroup --hidden
      \ --ignore .git
      \ --ignore .svn
      \ --ignore .hg
      \ --ignore .DS_Store
      \ --ignore "**/*.pyc"
      \ -g ""'
</pre>

It's taken [straight from here](http://blog.patspam.com/2014/super-fast-ctrlp). The cool thing about this trick is it doesn't just speed up indexing, it completely removes the need for it. This is achieved by relying on the command-line tool [Ag, aka Silver Searcher](https://github.com/ggreer/the_silver_searcher). It's a brilliant grep replacement I would recommend to anyone, being exponentially faster than grep (as in, you can happily search a whole hard drive in real time).

I've used Ag for years but never realised it could be piped into Ctrl-P!

That page also includes some matching optimisation, but seriously the Ag trick was all I needed. Searching is now completely instantaneous and I never need to worry about the index going stale again.

The update has been [pushed to my dotfiles](http://github.com/mahemoff/dotfiles).