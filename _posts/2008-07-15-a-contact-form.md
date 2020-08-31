---
id: 463
title: A Contact Form
date: 2008-07-15T11:03:01+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=460
permalink: /a-contact-form/
dsq_thread_id:
  - "375573820"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Ajax
  - Announcement
  - Captcha
  - PHP
  - Project
  - Twitter
---
I recently got fed up of spam. Well, that happened a long time ago. What bothered me recently, enough to take action, was false positives, i.e. real email that fell into my spam folder. My primary email address, michael@mahemoff.com, gets about 3000 mails a day...so what goes in my spam folder, stays in my spam folder. There's no way known I will ever fish it out.

People I know usually get through to me okay, but of course I also receive mails from people I don't know - who found my mail from my blog, websites, writings, or offline meetings. For them, there's a good chance of being marked as spam, especially if they use a subject line like "hello" which is a perfectly natural thing to do when you're just checking in with someone you've met at a conference, for example, so you can keep each other's contact details. (Incidentally, I still find it astonishing how many people maintain blogs - many of them meticulous, comprehensive, and full of goodness - but include zero contact info.)

So I finally bit the bullet and <a href="http://contact.mahemoff.com">made a little PHP/Javascript contact form</a>. It's been working great for several months now. This kind of form is nothing new, of course. Mail forms were once ubiquitous in every book on CGI. But there were a few modern twists worth mentioning.

The form looks as follows:

<a href="http://contact.mahemoff.com"><img src="http://picupper.com/2008/07/14/contact.png" width="98%" /></a>

The gnarly twists:

<ul>
<li>Captcha. Or, really, <a href="http://recaptcha.org">ReCaptcha</a>. Actually, I prefer Captcha to ReCaptcha - I think the benefit of scanning books is great, but can't justify the usability cost of having to enter two words instead of one (for no extra security benefit). Still, I wanted to try out ReCaptcha, and I also like the way its a popular, centralised, service, which means it should be better at detecting evil clients than a standalone library installation. <a href="http://recaptcha.net/plugins/php/">The PHP plugin and instructions</a> turned out to be incredibly easy to follow. A pleasant surprise that meant spam prevention took about 20 minutes to set up in total.</li>
<li>SMS option. Instead of email, you can send the message as SMS (text message to my phone). I need to improve the UI here a bit, ideally creating separate tabs for SMS and email. Anyway, the way this works is via everybody's favourite micro-blogging service, Twitter. On the Twitter website, I set preferences so direct messages are routed to my phone as SMS messages. Ideally, I would then send a direct message to myself each time someone wants to SMS me. But unfortunately Twitter doesn't let you send messages to yourself (silly!), so I created a secondary account (the venerable "mahemoff1"). Each time someone submits a SMS, I use the Twitter API to end a direct message from the secondary account to the primary account. This gets me a text message several seconds after the form is submitted. I also receive a copy in my Twitter account, as a bonus. (For all the talk about Twitter's unreliability, its text messaging is lightning fast. It shows up on my phone long before it shows up on Air clients, which only poll once a minute or so. Ideally I'd upload a video if I had the time, to show how quick it is.)
<li><a href="https://chat.mahemoff.com">A web chat facility</a>. Everyone should have it, to avoid making people install AIM etc just to chat with you one time! I installed <a href="https://blueimp.net/ajax/">an open-source chat client</a> so anyone can talk to me. In an ideal world, browsers would notify me when someone is trying to chat, but for now, it requires pre-arrangement. I would like to enhance the app so it uses the same SMS mechanism to tell me each time someone enters the chat room. 
</li>
</ul>