---
id: 1676
title: Social Delegation
date: 2012-06-01T22:15:02+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1676
permalink: /social-delegation/
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - API
  - Developer Experience
  - Klout
  - Parse
  - Social
---
Social may have been a buzzword for several years, but it's actually very primitive from a developer's perspective. As an app developer, all I can really do is let users log in and inspect their properties. Here's what I actually want to do ...

### Delegate The Karma

Points (StackOverflow, Reddit) aka Karma (Slashdot, Hacker News) is a neat social pattern. There's a gamification aspect to it obviously, but what I'm especially interested in is the permissioning aspect. As you progress up the ladder, you get more and more permissions to the point where you're pretty well part of the team. This is a more elegant permissioning model than specific roles such as "guest" "contributor" "admin".

The problem for users, though, is they're always back to square one. They can't bring their reputation with them other than a token link to Somewhere Else On The Web You Probably Won't Visit, which rather well defeats one of the original points of federated identity. And from the app developer's perspective, there's two further problems. Firstly, it damn well takes time to build all this! It's not 1999 and I don't have an army of code monkeys to bang out anything on a whim and another army to monitor funny business. And secondly, the chicken-egg problem. For a site in its tender youth, there's not always enough activity for users to build karma and certainly not enough to build the outer loop of meta-moderation.

Well, one lean approach would be to just do that which doesn't scale. Namely, give your mates karma, and anyone else you're talking to who seems half-savvy. That's perhaps the best thing you can do right now. But a better approach would be to delegate karma to a third party. What would such a third party look like? It would need some quantifiable measure of karma, an  API, and really some notion of exactly what this user is good at. No point letting users run wild on your pistachio content if they're specialists at chocolate.

The service already exists: Klout. And PeerIndex, Kred, and very likely Google Plus and Facebook under their respective covers. Klout is just PageRank for people after all, with all of the gaming and spam detection that comes with it. (These services are mostly vilified by people who are confusing flaws in their current implementations with the principle behind them and people who haven't dealt with the considerable classes of problems they solve for enterprises. Let's just assume they are generally reasonable services for now.)

So a solution is to keep your users' Klout up to date. Sync all users' Klout weekly and permission them accordingly. As your system grows, you may also build your own karma system up. Or even better, contribute your users' karma - with their consent - back into the Klout pool.

### Delegate The Groups

Social? Hello? Social should surely be about individuals banding together to form groups. Google Plus gets this right by baking in the notion of circles, though as [I've often griped](https://plus.google.com/106413090159067280619/posts/1xZcGpxEtLe), Google's notion of circles is more geeky than the average individual cares for, in much the same way wave's hierarchy was more complex than most people want to think about. It should be first and foremost about fixed groups, maintained by an admin.

I don't want groups in my own system. I don't want a manager to have to go around to every new system and enter the emails of their 15 direct reports. I don't want the football captain to have to enter his 30 team mates into my system for the umpteenth time. Let the group live somewhere else and I'll deal with it.

So a solution is to identify a platform for groups, make sure your user is the same guy or gal managing said group, and let them give permissions to that group on your own system. Sync the group regularly.

### Delegate The Relationships

Seriously man, every time I upload a slide to slideshare, I get a week of "Xyz has started following you on SlideShare". WAT? I have a social network for slides! This is unacceptable. I don't know if their real people or spammers (if the former, don't get me wrong, thanks for the interest in my slides and now we can be slide buddies. No, wait ...) But either way, I'm not going to click on their profile and Visit Their Site Somewhere Else On The Web to work out if I should invite them into my inner sanctum of people I share slides with.

Here is where Lanyrd got it right by just making your conference network your Twitter network. In the same way, it might be useful to see what your Facebook buddies are doing too. And so on. Facebook and I think G+ help a bit here by incorporating friends' info into their Like/+1 buttons. ie "Joe, Sue, and 7 others liked this". You may need more than that though if you're baking this right in.

So a solution is to sync social networks.

### Delegate The Profiles

"Hi I'm Michael and this is a new profile I wrote especially for this here basketball site because my football profile was wholly inadequate". Okay again you see where this is going...pull that profile content in from other sites, at least as a default. The ever-parsimonious Josh Schachter plays this gambit nicely with his latest project, [Skills.to](http://www.skills.to/). And pull in those Sites From Somewhere Else On The Internet too, so our intrepid user doesn't have to  enter their flickr URL yet for the tenth year running.

A special case that bears mentioning is avatars. This particular piece of developer experience suckage requires the developer to repeatedly poll the social API for the latest URL of the avatar, and then replicate the avatar, perhaps on S3, in order to avoid the sin of hot-linking. (It's not actually clear if sites like Twitter allow hot-linking of avatars, by the way. Please make that clear, Twitter and friends.) A service I used on Twelebs was Joe Stump's [Tweet Imag.es](http://tweetimag.es), but it's always been a kind of beta project and I've found it's sometimes delivering blank images. And fair enough, it's free and experimental. I'm pleased to see there's a new service out today that may actually solve this problem: [Cloudinary](http://cloudinary.com/) is an image-URL-manipulation tool, something I've thought about building myself for years, after once creating [a gradient generation tool](http://softwareas.com/imagemagick-one-second-gradient-images) and, later, [Faviconist](http://faviconist.com).

Bottom line is, sync your users' profiles.

### Now Don't Make Think, Consarn It! This Stuff Should Be Easy

If I wasn't focused fully on Player FM right now, I'd be building a system to make all this easy for developers. Right now, it's a ton of work, and really, it's all generic stuff. As you probably noticed, it's mostly just "here's some data, now let's just keep it up to date". So, you know, let me drop in a Rails gem and said gem just automatically keeps all this stuff in the database up to date "for free". Man would I pay you real dollar bills for that. I'm hopeful services like [Parse](https://www.parse.com/) might actually do this. I'd also suggest that any platform that provides these services - Klout, Twitter, etc. - should be mobilising their developer relations to make these kinds of libraries happen. Platforms are a huge battleground right now, and the winners will have to do more than offer raw RESTful services. They'll need to encourage frameworks and libraries that make the sync "just work".