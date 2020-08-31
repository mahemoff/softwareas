---
id: 774
title: 'Micropayments: What Portable Devices May Bring'
date: 2010-01-27T11:16:26+00:00
author: admin
layout: post
guid: http://softwareas.com/micropayments-what-portable-devices-may-bring
permalink: /micropayments-what-portable-devices-may-bring/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574583"
categories:
  - HumansAndTech
  - SoftwareDev
---
Amid the tablet hype is an interesting article from Derek Powazek - <a href="http://powazek.com/posts/2234">http://powazek.com/posts/2234</a>:

"""
I've been thinking about how to make money from online content since I launched Fray in 1996. Really, I can't tell you how many nights I've sat up, obsessed with it. It's been my white whale. And here's what I've come up with: a little bit of advertising works, so long as it's classy, and sell some paper if you can. But any plan that includes walling off your content from the rest of the web is destined to fail, unless it's porn of some kind (financial data is a kind of porn).

Why? It's not because everyone online is a cheapskate. It's because consuming content offline is still a much better experience. Leafing through a glossy magazine is simply sexier than clicking through a PDF

....

Apple could release a device that makes consuming media fun, is able to show any PDF beautifully (just like the iPod would play any MP3), and offers new media for sale in the iTunes store. If they did it right, publishers like me might finally be able to sell something digital that people would actually buy.
"""

Powazek is getting at some kind of payment for premium tablet-formatted content. I'm not too sure it could work, but it does make me think about micropayments.

Most of the talk about content is about buying books and subscribing to newspapers. Those are traditional business models applied to the web - paying hundreds or thousands of cents. Even that would be an improvement for publishers, who are forced to rely on ads right now.

But what if Apple took the in-app payment model and applied it to microcontent? Built that sort of thing into the core browser and viewing software? You'd end up with something like Jakib Neilson's 1998 vision of micropayments (<a href="http://www.useit.com/alertbox/paymentinterfaces.html">http://www.useit.com/alertbox/paymentinterfaces.html</a>) - and note he's talking about touch-screen gestures:

"""
Very cheap costs of maybe less than a cent per page would be invisible in the user interface. If it would cost half a cent to follow a link, then that link should probably be shown in exactly the same way as free links. The time to consider the payment would be more expensive than the payment itself, so the payment should be hidden for the user (except, obviously, for appearing on the monthly statement from the payment service).

Slightly more expensive costs of maybe 1-10 cents per page could be visualized by a simple glyph, a slight color change for the link, or by having the cursor show the cost as a pop-up when the user points to the link. It would also be reasonable for the user's computer to contact a reputation service to gather information about other users' experience with the link: If most other users felt that the destination page was not worth the cost, then a dialog box stating that fact should be shown if the user tries to activate the link. If the destination page has a good reputation rating, then it would be a waste of time to show the dialog box, and the user would be taken directly to the page if he or she activated the link.

Expensive pages costing more than maybe 10 cents would always require the user to click "OK" in a confirmation dialog before the cost was incurred.

Very expensive actions costing more than maybe $10 would require a different interaction technique than simply clicking an OK button since users often do so automatically without reading the warning text. An unusual interaction should be employed to make it clear to the user that a major expense was about to be authorized. The figure shows one of our ideas for a way of authorizing a payment: the system would show an image of a check with the cost and payee filled in. The user would authorize the payment by a sweeping gesture across the signature field, which would cause a digitized image of the user's signature to appear. Ideally, the sweeping gesture would be done by actually touching the user's hand to the screen, but it would also be possible to use a mouse gesture on systems without a touch screen.
"""

There would also need to be some settings to cap daily spending and perhaps cap spending on a particular domain.

Will Apple do it? Probably not on Day 1. There's much more low-hanging fruit. But they do have all the pieces in place to do it some day - they control mobile safari and the surrounding OS, the platform has users' trust, and most importantly, they can charge micropayments seamlessly.

Will others do it? I hope so. I'd love to see this experiment play out.

Will it work? Yes, I think there's something here. Powazek says walled content isn't possible on the web, and his solution is that user's will pay for a premium view of the content. I'm saying walled content *could* work if it was embedded into the fabric of the web *and* it gave you Powazek's premium view. You could imagine a free, high-quality, article on the league website about tomorrow's football final. It lists all the players, along with a thumbnail. Clicking on any player will set you back 10 cents - the browser subtly indicates it without obtrusively confirming with you when you click. For the 10 cents, you'll get a tablet-customised view of your player. It hooks into phone settings - you can save the picture as your screen saver and switch your voicemail prompt to be a recording from the player. (This is much cheaper than it would cost if it were a standalone app today, but the app store itself shows that selling lots of cheap units may be a more profitable strategy than a few expensive units.) And it hooks into other apps - sports geeks can export the player's stats into their spreadsheet app.

What lives at the URL of premium tablet content, when you're not viewing it on a tablet? That's the million-dollar question. On the one hand, you could say nothing, but then purists will argue it's not part of the conversation and people won't end up visiting it. Fair point, though I think there could still be enough interest if the landing page is high-quality enough to attract links and search results. On the other hand, the ideal thing is really progressive enhancement: the page still lives, the content is the same, but the tablet renders it. The good thing is the flexibility: website owners could make their own mind up about how to degrade, and the market will eventually learn what's best.

People will pay a lot for content in the right form. A few years ago, the same teenagers who refused to pay for high-quality renderings of their favourite bands songs, were the same teenagers who forked out big bucks for rubbish-quality ringtones. If the tablet is a fun device to hold and surf, people will pay for tablet-formatted content.

One of the problems with a plain-old subscription model is it goes against the model of the web as a series of interconnected nodes. It's silo-based. A micropayment model, where any page can charge a fee, might get over this problem. It does still have the grey cloud over it: will users want to constantly be making decisions about what they're looking at? If nothing else, it might detract from the experience. That's why the industry might evolve more into a Spotify-style "all you can eat" model. The tablet manufacturer (e.g. Apple) charges users $10/month for "premium web content"; perhaps it's included in the purchase, depending on how the plan works regarding 3G payments. Of the $10, it keeps $3 for itself and divvies up the remaining $7 equally to the owners of all pages the user visited that month. Users might see a small star icon somewhere while viewing premium content, just so they know they're getting their money's worth. 10 bucks a month to see content in premium form on a device you love? Even if the raw content is freely available without the payment, I could see this model working.
