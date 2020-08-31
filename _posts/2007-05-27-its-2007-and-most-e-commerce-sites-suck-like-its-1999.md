---
id: 377
title: 'It&#8217;s 2007 and Most E-Commerce Sites Suck Like It&#8217;s 1999'
date: 2007-05-27T00:19:26+00:00
author: admin
layout: post
guid: http://www.softwareas.com/its-2007-and-most-e-commerce-sites-suck-like-its-1999
permalink: /its-2007-and-most-e-commerce-sites-suck-like-its-1999/
dsq_thread_id:
  - "375573298"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - E-Commerce
---
<a href="http://flickr.com/photos/99195640@N00/121385021/"><img src="http://farm1.static.flickr.com/39/121385021_195d7becc2_d.jpg" width="400" height="320"></a>

<em>If I had a dollar for every time I clicked on an E-Commerce ad and got nowhere fast, I'd be a ...</em>

Rephrase

<em>If Google had a dollar for every time I clicked on an E-Commerce ad and got nowhere fast, *they*'d be a billionaire.</em>

That's better and just about close to reality.

After two unsuccessful attempts at purchasing from a major UK retail site, I'm giving up with it. I've also had similar frustration with several smaller sites too. Online stores need to get a few clues about session management - they need to be a bit smarter than the default behaviour of whatever COTS or programming framework they're using!

<ul>
<li><strong>Let me add to the cart before logging in</strong> Do you really think I'm going to go through registration just to add a product my cart, when I don't know I'm purchasing yet? See <a href="http://ajaxpatterns.org/Lazy_Registration">Lazy Registration</a>.</li>
<li><strong>Remember my cart for weeks and months, not 30 minutes!!!</strong>You're dealing with a planet of attention-deficit surfers with 12 browser tabs open. It's not like they're going to sequentially walk through your standard workflow like good little consumers - they're going to browse a bit, do some IM, add a product, check their MySpace comments, browse some more, poke a Facebook mate, wash, rinse, repeat. As your faithful logs will tell you, most people who add a product to the cart won't actually proceed to order it. So the next time they visit, wouldn't it be better if the product was still in the cart?
<li><strong>And yet, keep what's private, private</strong> The previous point may seem curious: if the cart is remembered for a month, then surely anyone who had access to the computer could go and access this user's account details - see their credit card, address, and previous purchases. After all, isn't that why sites log you out after 30 minutes. Actually, not quite. This is why I said <strong>E-Commerce sites need to get smart about session managemnet</strong>. Look how Amazon does it: there isn't a dichotomy of "logged in" versus "logged out". It's more subtle than that - more like a trichotomy: "fully logged in" (I can see and do everything) versus "semi logged in" (I get personal recommendations and my cart, but if I want to buy or view my account details, I need to re-enter my password) versus "anonymous" (I'm not associated with any user account. Even then, Amazon's still smart enough to give me personal recommendations and a cart I can manage.)
<li><strong>When I log in, retain my cart info</strong> Huh? But once I log in, aren't I a different user from that anonymous surfer? From a rigidly technical view, maybe. But the server still knows you're the same person, or can do if it's smart enough. So the items I added while browsing anonymously should then be added to whatever items were in my long-term cart. Again, it means being a bit smarter about session management.
<li><strong>Don't make me register.</strong> Let me purchase something without registering. The reasoning should be obvious.
<li><strong>Provide full pricing info.</strong> E-Commerce sites have sophisticated price calculation algorithms that come into use when you go to purchase, but provide no information prior to that. I know there will be a marketing argument about hiding that information, but even then, it could still be hidden away in a document somewhere as long as it was available to someone curious to go searching for it.
<li><strong>Make Proper landing pages for ads</strong>Amazing that this still happens, but about half of the time you click on a Google ad, you're taken somewhere silly like the homepage instead of the product in question, or at least a site-specific search for that product.
</ul>

Summary: Most E-Commerce sites still suck and haven't learned much since the late '90s.
Corollary: This is a lucrative industry with plenty of opportunities.<!--cc2c5756b2b5583a22292bfcf9f7c887-->