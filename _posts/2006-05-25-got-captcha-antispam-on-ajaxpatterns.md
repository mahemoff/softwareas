---
id: 303
title: Got Captcha? Antispam on AjaxPatterns
date: 2006-05-25T23:08:20+00:00
author: admin
layout: post
guid: http://www.softwareas.com/got-captcha-antispam-on-ajaxpatterns
permalink: /got-captcha-antispam-on-ajaxpatterns/
dsq_thread_id:
  - "375572909"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Captcha
  - Links
  - MediaWiki
  - Patterns
  - Spam
  - Wiki
---
I've been blabbing on about how I'm going to open up the AjaxPatterns wiki for as long as it's been online (about a year), blah blah, talk is cheap. Anyway, it's a few steps closer now. The main issue has been protection against spam - some entrepeneurial folks behind numerous proxies have discovered there's a good niche market among Ajax developers for fake watches and cheap pharmaceuticals, and AjaxPatterns is just the thing for their cunning Long Tail marketing strategy. I wish these measures weren't necessary, and they certainly won't be foolproof, but hopefully they'll let us grow a bunch of useful Ajax content without too much interruption. After The Ajax Experience, I realised how much more there is left to document and how much people want to hear and say.

So these are a few things you'll see at <a href="http://ajaxpatterns.org">AjaxPatterns</a>.

* <b>Captcha</b> - just implemented. Let me know if you have any problems. Unfortunately, it does go against <a href="http://ajaxian.com/archives/accessibility-use-ajax-get-sued">accessibility</a>, but contributors who have difficulty with it could always mail me contributions. Hopefully, mediawiki will incorporate captcha at some point, the kind of project where the resources for a more accessible solution would make sense. <a href="mailto://michael@mahemoff.com">Mail me</a> if you want more info on the implementation.<br/><a href="http://ajaxpatterns.org"><img  src="http://img475.imageshack.us/img475/1278/ajaxspam3hn.png"/></a>
* <b>Links to book version</b> Implemented, but not live. Each pattern page will link to the corresponding book version (well, a close-to-complete draft). Even if a spammer messes with the pattern description for a short time, there will be a permanent link to the corresponding description in the book.
* <b>Word/URL BlackList</b> Based on <a href="http://meta.wikimedia.org/wiki/Talk:Spam_blacklist">Spam Blacklist</a>. Sorry, no examples involving discount Rolexes.
* <b>Backup strategy</b> Another measure is frequent snapshots of the whole thing (that's always been there)
.