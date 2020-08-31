---
id: 2001
title: 'Don&#8217;t API All The Things &#8230; The Downside of Public APIs'
date: 2014-12-28T10:17:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2001
permalink: /apis-considered-harmful-maybe/
categories:
  - General
  - SoftwareDev
---
Paul kicked off an interesting conversation about [pros and cons of a public API](https://twitter.com/Paul_Kinlan/status/548935527341494272) [1]. The benefits of APIs have been well-cited, certainly valid, and I would also argue in favour of public APIs in many situations. Yet startups like Uber and WhatsApp managed to grow to stratospheric heights without any API. Which begs the question often ignored in some API-gushing circles: In the ROI equation, **what are the downsides of publishing an API**?

_This is a deliberately one-sided post as I wanted to make a reference of all the downsides in one place._ Following are the potential cons that should be considered in any pros-versus-cons API feasibility analysis:

* **Friction and lock-in** - APIs are notoriously difficult to upgrade as clients don't want to keep updating their code. So once you publish a production-ready API, you have a long-term commitment to maintain it even as you grow and shift the underlying functionality.

* **Server load and quality of service** - Of course, your servers are going to be doing more work when 50 other clients are connected, or 50x clients if the API clients' end-users are communicating dirctly with your API. (OTOH they might be unofficially scraped in the absence of an API, in ways that may be even worse because you can't fully consider cacheability and anticipate what will be called.)

* **Need a higher-quality API** - Before your API is public, you can "fake it till your API makes it". Meaning that you can put logic in your clients which should really be on the server, but because of other priorities or implementation differences, it's easier to do a quick job in the client(s) [2]. (Which is fine as long as security-critical functionality like input validation still happens on the server.) 

* **Developer Experience cost** - There's no point putting out a public API unless it's going to be adopted by developers and continuously improved in response to real-world experience. That requires good API design, documentation, developer engagement, and issue tracking. Extra work.

* **Conflict of Interest** - An API invites competing apps *cough* Twitter *cough* or even apps that combine several services and thus turn you into a commodity [3]. If you're a pure "API company", e.g. Stripe or Twilio, that's par for the course. If you are more of a UX/app company, it may be an issue depending on your business model. If you're heavily ad-based and not interested in charging developers, like Twitter, then yes it's an issue that someone can make a good app without ads. If it's based on a charge for server-side services, e.g. Dropbox, then no it's not much of an issue that there are alternative Dropbox apps around [4].  Guardian's API is an interesting example of a [hybrid model](http://www.theguardian.com/open-platform/faq) which allows the provider to have similar incentives to the developer, at the expense of extra complexity.

* **Distraction** - As well as the extra effort required, the API and surrounding developer relations is adding another department to the organisation, and therefore a new source of management distraction.

Most companies can and should deliver public APIs at some point and for some functionality. None of the points above argue against that, but should give pause to anyone blindly following the 2010-era doctrine of "API All The Things".

**Notes**

1. "Public" APIs because I take it as a given that any cloud service has a private API. That's just a truism. Whether companies frame it as an API and benefit from principles of public API design, that's not always the case, but they have some API either way.

2. For example, [Player FM's](https://player.fm) Android app does some search filtering to remove junk results because until recently, the server didn't provide that.

3. When Uber did release its first very limited API, it added an exclusivity clause, meaning apps can't also use Lyft etc APIs, so it avoids direct price comparisons. TweetDeck was also on this path, with its Facebook integration, as was FriendDeck from none other than the man who inspired this post, Paul Kinlan.

4. It's still an issue as some of those apps could turn around and provide a one-click conversion to Box, GDrive, etc. But far less concerning that for Twitter, the worry of a stunning Twitter app that doesn't show ads