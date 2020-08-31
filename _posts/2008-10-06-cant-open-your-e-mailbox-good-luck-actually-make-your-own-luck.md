---
id: 490
title: '&#8220;Canâ€™t Open Your E-Mailbox? Good Luck.&#8221; Actually, Make Your Own Luck'
date: 2008-10-06T09:44:47+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=487
permalink: /cant-open-your-e-mailbox-good-luck-actually-make-your-own-luck/
dsq_thread_id:
  - "389988946"
categories:
  - SoftwareDev
tags:
  - GMail
  - Webmail
---
New York Times has a popular article about an important topic: <a href="http://www.nytimes.com/2008/10/05/business/05digi.html">getting locked out of your webmail account:</a>

<blockquote>
LOGGING on to Gmail or other e-mail service has become a routine of daily life, completed without a thought. What would you do, however, if you woke up tomorrow, plugged in your user name and password as you always do, but then received an unfamiliar message: â€œUser name and password do not matchâ€?

If youâ€™re a Gmail user, what youâ€™ll want to do after a few more unsuccessful, increasingly frantic attempts is to speak with a Google customer support representative, post haste. But thatâ€™s not an option. Google doesnâ€™t offer a toll-free number and a live person to resolve the ordinary userâ€™s problems. 
</blockquote>

The gist is, if you want GMail with the assurance you won't get locked out, pay up $50 a year for support.

$0/year is very reasonable, but there's a way you can do it for free, and quite simply. You just sign up for <a href="https://www.google.com/a/">Google Apps for Your Domain</a> (note: I'm not a shareholder nor an affiliate, just a fanboy). The catch is you have to own a domain, but (a) they are damn cheap, around $7/year for .coms; (b) it doesn't even have to be a .com;  some other endings like spam-infested .biz and .info are even cheaper; (c) you may already own a domain anyway. (A friend recently showed me a great little website some had put together for his business, with its own domain, but the email was a yahoo! address - more professional to match it to the website ne?)

With Google Apps for Your Domain, you point your DNS server's MX at Google. If you're locked out, you can point your MX at another mail server, perhaps your SNS registrar provider as most of them provide some rudimentary support. And you're unlikely to be locked out anyway, because you can post a special message on a website on your domain, to prove you control it, which will reset the domain admin password. This is all offered free of charge.

Admittedly, this is not a mom-and-pop solution. It's obviously requires some tech knowledge to own a domain and point its MX somewhere or post a message to it. But certainly doesn't require hardcore geek-fu either, just a little savvy and willingness to try things out and follow some instructions. If you already own a domain, you may as well go this route over just using a plain GMail/Yahoo account. it's great piece of mind to know that you, and only you, are the master of your own domain!