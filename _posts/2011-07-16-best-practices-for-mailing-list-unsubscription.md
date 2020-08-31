---
id: 1243
title: Best Practices for Mailing List Unsubscription
date: 2011-07-16T11:53:14+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1243
permalink: /best-practices-for-mailing-list-unsubscription/
dsq_thread_id:
  - "375283756"
categories:
  - General
  - HumansAndTech
tags:
  - Mailing Lists
  - Spam
  - UX
---
Having spent the past too many hours gearing up for inbox zero or some such, I'm pleased to say almost every mailing list now includes an "unsubscribe" links (even those which I never signed up to! Which I avoided clicking on as they are probably a dodgy way to get you somewhere else). I assume this is some requirement of Spamhaus etc which the lists must follow to avoid falling in the spam folder, which affects their spam status in GMail etc. Also, if lists make it hard to unsubscribe, users will mark them as spam, which is also detrimental to their status on GMail etc.

After hitting "unsubscribe" many times, here's what works well (of course, this is just from the perspective of an interested user):

* While most let me unsubscribe immediately, some require login. This is a bad move as I assume many users simply won't bother, especially if it's some list you signed up to years ago. Interestingly, those which unsubscribe immediately fall into different categories - some are off-site, so you can only unsubscribe. Others are onsite and once you unsubscribe, you're also logged in, which is possibly a security risk (maybe a reasonable one, but I don't think they've always considered this happens). In a few cases (e.g. LinkedIn I think), you can unsubscribe, but then you have to log in after that. A fine example of the awesome Amazon-style "semi-logged in" state.
* A good practice is to provide settings for what you want to receive. But not too many options! LinkedIn is particularly verbose with its new group feature - turns out each group has its own mail settings - a handful of checkboxes for every group. Just say no!
* Some have a delay of up to three days, which is not just an annoyance, but breaks the UX principle of immediate feedback. You unsubscribe, then you see a new mail a few hours later and think maybe you didn't unsubscribe after all.
* Automatic Unsubscribe is best, but as with all "shoot first, ask later" style interfaces (e.g. Auto-Save), you also want to provide an "Undo" facility. One list did that, with a "Did you really mean to Unsubscribe? <u>Resubscribe</u>". Smart.
* Some said "We're sorry to see you go" etc, but a smarter thing I saw was "You can still keep in touch with us on <u>Twitter</u> and <u>Facebook</u>".