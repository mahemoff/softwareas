---
id: 310
title: 'Teleporter &#8211; From Greasemonkey to Self-Contained Extension'
date: 2006-06-19T17:48:18+00:00
author: admin
layout: post
guid: http://www.softwareas.com/teleporter-from-greasemonkey-to-self-contained-extension
permalink: /teleporter-from-greasemonkey-to-self-contained-extension/
dsq_thread_id:
  - "384355287"
categories:
  - SoftwareDev
tags:
  - Amazon
  - Extension
  - Firefox
  - Greasemonkey
  - Javascript
  - Links
  - XPI
---
<p>My previous post outlined <a href="http://www.softwareas.com/domain-teleporter-greasemonkey-script">Domain Teleporter</a>, a first attempt at a GM script. Continuing the experimentation (as I have a comlpetely different real example in mind), I wanted to see how easy it was to create a self-contained FF extension from the GM script ... I figure there's a significant population who have FF and can't or don't want to install Greasemonkey, even if this leads to a functionally trivially extension.

<p><b>Converting a Greasemonkey script to a Firefox extension was stupidly simple, thanks to an online tool</b>, Anthony Lieuallen's <a href="http://www.arantius.com/misc/greasemonkey/script-compiler.php">User Script Compiler</a>. I'd read about it a while ago, and assumed there must be   some catch, but the conversion was indeed child's play ... enter your name and homepage, cut-and-paste the script, and submit. The XPI pops out immediately as a binary download.

<a href="http://www.arantius.com/misc/greasemonkey/script-compiler.php"><img width="500" height="200" src="http://img410.imageshack.us/img410/9343/teleporterextension4do.png"></a>

<p>FWIW, the extension is <a href="http://mahemoff.com/project/teleporter/">published here</a>; I used htaccess in the distro directory to ensure it will be an installable download (so it can be installed immediately, as opposed to saved locally) as follows:
<pre>
AddType application/x-xpinstall xpi
</pre>

The <a href="http://ajaxpatterns.org/Richer_Plugin">Richer Plugin pattern</a> talks about the importance of FF extensions and the like.

BTW The extension is Amazon Teleporter, not Domain Teleporter, because there's no longer any way to change the default "Amazon*" domain for which it applies - GM supports that sort of thing as a built-in feature; whereas an extension would have to implement it manually ... a lot more work, requiring a  custom-made options dialog and a persistence mechanism.