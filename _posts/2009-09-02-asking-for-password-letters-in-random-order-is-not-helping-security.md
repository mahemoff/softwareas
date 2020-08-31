---
id: 613
title: Asking for password letters in random order is not helping security
date: 2009-09-02T08:32:08+00:00
author: admin
layout: post
guid: http://softwareas.com/asking-for-password-letters-in-random-order-is-not-helping-security
permalink: /asking-for-password-letters-in-random-order-is-not-helping-security/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574398"
categories:
  - SoftwareDev
---
<img src="http://img.skitch.com/20090902-g2wumk1fankc9xubks166stq6.jpg" style="width: 400px" />

I get this every now and then from banking and other services. I
appreciate the principle of challenging you on certain letters, so the
entire password is never transferred. However:

- Please add an extra line of code to sort the positions. Asking me
for the 4th letter and then the 2nd letter doesn't fit the way I
think, and has zero impact on security anyway.

- It does get difficult when I'm walking around on my mobile and I
have to punch in the 8th letter of an 11-letter password.

- It's also fairly pointless on a SSL-secured website, where no-one
should be able to see the password - if someone is in a position to
sniff the password, they will probably be able to sniff it again the
next few times and get your details. It's only useful in a call centre
situation, to prevent casual abuse. You may as well do what other
sites do and ask for the whole password. The above screenshot is from
experian, which is probably more used to call centres and has just
translated their phone script into a website without thinking about
the different user experience and different conventions of the web.