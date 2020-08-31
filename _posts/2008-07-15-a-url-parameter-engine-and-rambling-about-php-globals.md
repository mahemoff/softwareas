---
id: 462
title: A URL Parameter Engine (and Rambling about PHP Globals)
date: 2008-07-15T00:44:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=459
permalink: /a-url-parameter-engine-and-rambling-about-php-globals/
dsq_thread_id:
  - "375573782"
categories:
  - SoftwareDev
tags:
  - Coding
  - PHP
  - REST
  - URL
---
<a href="http://picasaweb.google.com/jjranch22/Wales/photo#5181654982624695666"><img src="http://picupper.com/2008/07/14/longestname.jpg" width="350"></a>

I've recently been playing around with PHP again, because (a) <a href="http://softwareas.com/server-side-hosting-options">it's vastly simpler to deploy personal projects in PHP</a> than any other platform (aside from pure client-side Ajax of course!) (b) it's so easy to get simple stuff done.

Anyway, one thing I'm doing is creating a RESTful service where parameter crunching is at an all-time high. The ancient way this was done was with magically created globals. i.e. For the URL <tt>http://example.com?id=10</tt>, you would end up with a global called $id, set to 10. But the more contemporary way to do it is to use a global array called $_GET, i.e. <tt>$_GET[$id]</tt>. This is considered safer, to ensure malicious users don't set important globals. And in PHP 6.0, the former way is being obliterated altogether, since the relevant configuration option - <tt>register_globals</tt> is <a href="http://php.net/variables.predefined">being altogether removed</a>.

Well, to me, this is throwing out the baby with the bathwater.

This comes down to how you view PHP. For me, if I want to build a massive, complex, piece of software, I will use Rails or Java. So I consider PHP a scripting language and I value concise expression highly. Features like namespaces (to be added in PHP 6) and even OO don't mean all that much to me in this language. I am much more concerned with syntactic sugar.

Thus, I would prefer to see templates look like this:

[php]
Your name: <?= $name ?>
[/php]

... and not:

[php]
Your name: <?= $_GET["name"] ?>
[/php]

A little thing, but in the context of a large corpus of templates, each with many variables, it makes a big difference.

So I'm working on a little parameter-processing engine which will let me use the "evil" $globalVar notation, but in a way that requires each script to pass in a whitelist of acceptable variable names. It also has some other value-adds, such as passing in default values. And these default values can be other parameters that were passed in.

(Incidentally, even if I wasn't building this script, the first thing I would do would be to globally alias $G or to the uglier and more verbose $_GET.)

REST turns the URL into a command line, and this should push web framework developers towards smarter ways of processing parameters. <strong>Think <a href="http://en.wikipedia.org/wiki/Getopts">Getopts</a>, but for the URL instead of the shell command line.</strong> And that's where I'm heading.

<img src="http://picupper.com/2008/07/14/Billboard_1.jpg" width="350">