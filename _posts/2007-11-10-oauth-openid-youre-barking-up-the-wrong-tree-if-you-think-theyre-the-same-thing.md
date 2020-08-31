---
id: 408
title: 'OAuth-OpenID: You&#8217;re Barking Up the Wrong Tree if you Think They&#8217;re the Same Thing'
date: 2007-11-10T20:56:11+00:00
author: admin
layout: post
guid: http://www.softwareas.com/oauth-openid-youre-barking-up-the-wrong-tree-if-you-think-theyre-the-same-thing
permalink: /oauth-openid-youre-barking-up-the-wrong-tree-if-you-think-theyre-the-same-thing/
dsq_thread_id:
  - "375173299"
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"eaabd60c07f0";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:41:"https://medium.com/@mahemoff/eaabd60c07f0";}'
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Identity
  - OAuth
  - OpenID
  - Security
  - Web
  - Web 2.0
---
<a href='https://oauth.net/'><img style="width:125px; height: 125px; padding: 5px; display:inline;" src='https://i.imgur.com/8Y8UgNNl.png'></a>
<a href='http://openid.net'><img style="width:125px; height: 125px; padding: 5px; display:inline;" src='https://i.imgur.com/vxwIltq.png' /></a>

OAuth, OpenID...they sound like the same thing and they kind of do vaguely similar things But I'm here to tell you, <a href="http://oauth.org">OAuth</a> is not <a href="http://openid.net">Open ID</a>. They have a different purpose. I've been playing around with OAuth a bit in the past couple weeks and have a grip on what it's aiming to do and what it's not aiming to do.

To start with, here's what OAuth <em>does</em> have in common with Open ID:
<ul>
   <li>They both live in the general domain of security, identity, and authorisation</li>
   <li>They are open web standards. Created and evolved by people with an itch to scratch and evolved pragmatically by a loose, fluid, alliance. Think REST, not SOAP. Think Bar Camp, not The 25th Monosemiannual International Convention for the Society of Professionals who Devise Acronyms Quite a Bit.</li>
   <li>They both celebrate decentralisation. There is no central Open ID or OAuth server that holds all the security information in the universe (cf Passport). Anyone can set up as a server or a client.</li>
   <li>They both involve browser redirects from the website you're trying to use - the "consumer" website - to a distinct "provider" website, and back again. Meanwhile, those websites talk to each other behind the scenes to verify what just happened.</li>
  <li>The user can actively manage the provider website, exerting control over which websites can talk to it and for how long.
</ul>

With that much in common, the casual observer could be forgiven for confusing them. But they're different. Not different as in "vying to be the no. 1 standard", but different as in "they let you do different things". How so?

<strong>Open ID</strong> gives you one login for multiple sites. Each time you need to log into Zooomr - a site using Open ID - you will be redirected to your Open ID site where you login, and then back to Zooomr.
<strong>OAuth</strong> lets you authorise one website - the consumer - to access your data from another website - the provider. For instance, you want to authorise a printing provider - call it Moo - to grab your photos from a photo repository - call it Flickr. Moo will redirect you to Flickr which will ask you, for instance, "Moo wants to download your Flickr photos. Is that cool?", and then back to Moo to print your photos.

With OAuth, you still need to log into the provider. e.g. When Moo sends you to Flickr, you still have to log into Flickr (or be logged in already). How Flickr decides you're logged in is completely orthogonal to OAuth. It could be a standard username-password login, it could be via a physical password device, or it could well be via Open ID.

With Open ID, there is no suggestion of two web apps sharing your data. Except in the very limited sense that the Open ID provider may hold some general information about you, e.g. some photos, addresses, phone numbers, etc., and with your consent, send it back to the consumer so you don't have to re-enter all the boring profile details again. However, this is data of a generic, non-application-specific, nature. (And even this limited form of sharing is an extension to the core Open ID spec.) With OAuth, any information you hold on any website can be shared with another website. You could share your GMail with a clever consumer that automatically tags items by inspecting the content, if GMail was an OpenAuth consumer.

Or you could copy your GMail address book into Facebook, by allowing Facebook to read your GMail account. Right now, the only way to do that is to give Facebook your GMail username and password. Clearly a dumb thing to do, and that's exactly the kind of thing OAuth is set up to prevent. OAuth prevents it by explicitly asking you if you want to let Facebook grab your details from the provider. That's not a problem Open ID solves. Even if Facebook and GMail used Open ID and you had accounts with both against the same Open ID, you still couldn't get Facebook to read your GMail account. The Open ID provider wouldn't let Facebook log in to GMail as if it was you. Even if an Open ID extension came along to allow it, you wouldn't want it. It's too coarse-grained and would allow the consumer to do too much potential damage. OAuth is more fine-grained - consumers can do some things with your provider data, not everything.