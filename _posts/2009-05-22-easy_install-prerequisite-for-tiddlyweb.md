---
id: 540
title: 'easy_install: Prerequisite for TiddlyWeb'
date: 2009-05-22T13:39:01+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=537
permalink: /easy_install-prerequisite-for-tiddlyweb/
dsq_thread_id:
  - "412775867"
categories:
  - SoftwareDev
tags:
  - Osmosoft
  - Python
  - SetupToolsl
  - tiddlyweb
---
Done a few TiddlyWeb installs now - here's a tip. It's easiest done with easy_install. This is a tool that installs or upgrades everything "in a click", except that installing easy_install isn't really easy; the Python community could learn a lot from the Rails community about how to make downloading and installing easy, for those who aren't intimately familiar with the underlying technology. (Summary: I google for the tool, I click on the first result, and I see a big fat download button).  If you try to look up easy_install, also called "easyinstall", you'll find it's actually included with "setuptools", and you'll find a website that makes you go around in circles if you click the links you think you're meant to click. What you might not find is the package you need as the downloads are buried down the bottom of <a href="http://pypi.python.org/pypi/setuptools#installation-instructions">

For a Mac at least, get easy_install with the following steps:

* <a href="http://pypi.python.org/pypi/setuptools#installation-instructions">Download setuptools from the bottom of this page</a>. Just get the tarball. (like "curl -O http://pypi.python.org/packages/source/s/setuptools/setuptools-0.6c9.tar.gz#md5=3864c01d9c719c8924c455714492295e", but check that link for the latest version)

* extract it - tar zxvf setuptools-0.6.......tar.gz

* sudo python setup.py install

* Cool, now go read <a href="http://cdent.tumblr.com/post/94180697/tiddlyweb-for-the-impatient">Chris Dent's notes on installing TiddlyWeb</a> or <a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers/Installing%20on%20CentOS%20Behind%20a%20Corporate%20Firewall">various</a> useful <a href="http://tiddlyweb.peermore.com/wiki/recipes/docs/tiddlers/Troubleshooting%20easy_install">things on the wiki</a>.