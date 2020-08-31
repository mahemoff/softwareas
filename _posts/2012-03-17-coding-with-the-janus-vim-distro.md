---
id: 1586
title: Coding with the Janus Vim Distro
date: 2012-03-17T13:21:37+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1586
permalink: /coding-with-the-janus-vim-distro/
categories:
  - SoftwareDev
tags:
  - IDE
  - Vim
---
I'm back on Vim, let me explain why and what my setup is.

## Janus Vim Distro

The background is I've been happy, bordering on ecstasy, to use Vim for small projects, but found file management difficult for larger projects. I installed the incredibly useful [Janus Vim distro](https://github.com/carlhuda/janus) a while back. There's a one-liner curl script provided to install Janus.

The first useful thing about Janus is it ships with a selection of vital coding plugins. The most useful so far have been: NERDTree for file management; Ctrl-P for locating files (using IntelliJ-like matching, e.g. "PropertiesController.rb" could be found with "PCo" or "PrC"; "stars.html" could be found with "st.h", and with its Most Recently Used algorithm, gives the same sense of magic); Ack for quick ack/grep-like searches; Syntastic, which automatically red-flags syntax errors when you open or save a file (ideally I'd like to run automatically every few seconds).

Janus also ships with a bunch of useful macros, as well as some handy customisations for those default plugins it ships with. All this is nicely documented in :help janus.

Another nice thing about Janus is it sets up a sane directory structure for you. If you're not familiar, Vim's default config distributes packages across role-based directories (like the way Linux distributes a package into /var/log, /etc, etc). This makes it difficult to add and remove a single package. [Pathogen](https://github.com/tpope/vim-pathogen) fixes this by letting you have a separate directory for each directory, and Janus ships with a Pathogen setup by default. Fortunately, most Vim packages are re-distributed in Pathogen form somewhere on the GitHub. And Janus provides a ~/.janus directory where you can drop them in. You can also customise your vim setup with ~/.vimrc.before and ~/.vimrc.after.

## Command-Line/Terminal Vim (not MacVim)

Although the Janus README suggests using MacVim, I found it to be really slow switching tabs, at least while running with the Janus distro. So I've reverted back to regular shell Vim (which I installed via `brew install vim`). This is what I'm more used to anyway, as it has the advantage of fitting in with my regular workflow &mdash; I can just bring it up any time on the command-line &mdash; and it means I can use it as part of a multi-tab iTerm environment. So I can just cmd-left and cmd-right to drop into a running bash session. <s>What I still need to work out is how to use the mouse with Vim running in iTerm2 (:set mouse=a isn't working for some reason), which would give back the main benefit of MacVim.</s>

<i>Update:</i> Yes, mouse now works in terminal mode! Now I can click on tabs and the expand/collapse/open items by clicking on the NERDTree. It just needed <em>ttym</em> to be set in the end; I've verified this works for the default TERM setting of "linux" (I think it's default anyway). All you need is the following settings in your vim config (~/.vimrc.after in the case of Janus distro). I've only tested this in iTerm2.

<pre>
set mouse=a
set ttym=xterm2
</pre>

## NERDTreeTabs

When I tried Janus some months ago, one thing bugged me. It was the main reason I scurried off to switch to RubyMine. That thing was NERDTree, the file hierarchy system. So close to being useful, falls stunningly short at the last mile.

What's missing from NERDTree? It just doesn't behave how one expects or wants a file tree to behave. You open a new tab, and NERDTree is gone! Imagine if web browsers removed the tab bar every time you open a new tab! Unnatural, unwanted. Yes, you can set up auto-commands to make it be there when you open a new tab, but even then, you end up with a different instance of the tree each time. So what got me back on Vim was finding this plugin:

[NERDTreeTabs](https://github.com/jistr/vim-nerdtree-tabs)

Simply put, it gives the illusion that you're using the same tree everywhere. So you switch tabs (or open a new tab) and the file tree is exactly the same as in the other tab. Really, a file hierarchy is essential for a large project, even if I use Ctrl-P most of the time to switch files. So this discovery was good enough to get me back on Vim. I mapped it to ,n (, is my leader) with `map <Leader>n <plug>NERDTreeTabsToggle<CR>`.

A couple of caveats. First, there's still no way to keep the file tree in sync with the file you're working on. It would be cool to have NERDTree highlight the current file, for example, like the kind of sync behaviour most IDEs provide. Second, I haven't been able to open this automatically in Janus. So I have to manually close the NERDTree if it's open. (Somehow, NERDTreeClose and NERDTreeTabsToggle have no effect in .vimrc.after; I'm not sure how to customise Janus here to fix this.)

## Exuberant Tags

It's also worth using [Exuberant ctags](http://ctags.sourceforge.net/) for navigation. I installed it with `brew install ctags`. This lets you ctrl-] on a word to open up the corresponding file, and is also required for some of the default Janus plugins.

## Wish Me A Pony

There are loads of Vi emulators out there now. Separate ones for Eclipse, IntelliJ, Cloud9, and Sublime. I've never had much luck with them. One of the great benefits of Vim and command-line in general is the muscle memory. Everything is supremely predictable and it just flows. My experience with these emulators is I'm always second-guessing what happens if I type anything. It's not always clear whether I'm in command-line mode or not. And, they often require a lot of customisation to be usable.

My first wish is that someone would build a text editor/IDE with actual Vim inside it, not an emulator. It would ship with appropriate plugins to talk to its host IDE environment.

My second wish is that someone would use Chrome's Native Client to build a Vim textarea plugin. Imagine if you could just call $('textarea').vim() and every textarea becomes a Vim control. And not a Vim-in-JavaScript component. But &mdash; with the magic of Native Client &mdash; an actual Vim component. With such a component, people could build extensions for Vim enthusiasts to use Vim everywhere and cloud IDEs like Cloud9 could support the real-deal Vim.