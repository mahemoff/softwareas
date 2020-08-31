---
id: 451
title: 'Firefox 3: The Changes&#8230;Firefox 4: The Wishlist'
date: 2008-06-18T08:50:37+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=448
permalink: /firefox-3-the-changesfirefox-4-the-wishlist/
dsq_thread_id:
  - "375573744"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Browsers
  - FF3
  - FF4
  - Firefox
  - Usability
  - Web
---
<img width="300" src="http://picupper.com/2008/06/18/firefox-sport-car.jpg" />

<h2>Firefox 3.0 ticker tape parade</h2>

Today is Firefox 3.0 landing day. Maybe tomorrow as the servers have been down for many hours now. Funny how Twitter is up, but Mozilla is down...it feels like today is the Juneth of 18. Anyway, this is great news as you could wile away a few lazy hours tweeting and plurking about the irony and how you're chomping at the bit for FF 3.0, and watching other people say the same thing but with different yet equally charming emoticons. But anyway, FF 3.0 is pretty much here. Yay!

Firefox 3.0 is faster, more stable, and standards-based, and that's no mean technical feat, but the upgrade is not so obvious from a consumer's perspective. And my own ADD mindset craves more visible changes that will impact on usability and utility.

The modern browser is the application billions of users spend the most time in, many hours a day, and the trend is set to continue as desktop migrates to web. And Firefox is used by 18% of users (<a href="http://en.wikipedia.org/wiki/Usage_share_of_web_browsers">Net Applications via wikipedia</a>, Q2 2008) - that's 18% of some billions of users. A very big number indeed, and even more remarkable in certain markets, where Firefox dominates share, and even in the entire population of certain countries, <a href="http://arstechnica.com/news.ars/post/20080427-all-the-rage-in-europe-firefox-marketshare-climbs-higher.html">where it appears to be neck-and-neck with IE</a>. Furthermore, as a major player, the features of Firefox are clearly going to influence those in competing browsers. What's in Firefox matters a lot. So, by deludedly illogical inference, the present article must also mean a lot to the future of our green planet. Here I will outline UI changes in FF3, then present my wishlist for FF4.

<h2>But first, what's in 3.0 then?</h2>

This is a wishlist for the next version of Firefox, FF 4.0. But first, let's review Firefox 3.0, ignoring those important but not too tasty "-ility" updates, and instead focusing on what users will actually see. I had to think about this. After several months of using both versions alongside each other (on different boxes), I really don't notice much difference at all. <a href="The front-end changes, <a href="http://en.wikipedia.org/wiki/Mozilla_Firefox#Version_3.0">as noted by wikipedia</a>, are pretty trivial. (I noticed <a href="http://www.dria.org/wordpress/archives/2008/06/12/655/">a better list here</a>, though there are no other major features mentioned.)

* <b>More native look and feel.</b> Nice, but a small change.
* <b>Redesigned download manager, can search for downloads</b> Same.
* <b>Redesigned add-on manager</b><a href="http://mozillalinks.org/wp/2008/01/firefox-3-add-ons-manager-is-almighty-too/">It's integrated with the main distro site</a> This is by far the most important new feature. I'll elaborate later, but FF is all about plugins and the plugin process has been pretty silly up to now. In the book, Art and Science of Javascript, my chapter on Firebug included a section on installing the Firebug extension. And I can tell you, looking at it step by step, you can see how complicated the whole thing is.
* <b>Microformats are supported.</b> Cool, we like microformats and it leads the way to the so-called "Web 3.0"!
* <b>Introduced Places for bookmarks.</b> Yes, this is the most obvious new feature, but the thing is, years of rudimentary bookmarking support, combined with Google's almightiness and Delicious et al, has weaned me, and I suspect many others, off bookmarking in general. I don't know, how many people are really going to tag their bookmarks? What I do like is the new smarter address bar with history auto-completion and better display. It has leap-frogged IE here, which has searched by title for some time. Handy little feature.
* <b>OSX version supports Growl, spell check, and Aqua.</b> Well, Growl is nice and it's available to Add-on developers...but it should also be available to all websites, perhaps using a whitelist setup. (Similar to the Add-On trust system now - a notification panel that says "this application wishes to notify you of critical events via Growl. Do you agree?".)
* <b>Default icons change</b> Cool but fairly basic again.

These are all changes you might expect in a point release - it would be hard to justify going 3.0 in the absence of all the other improvements to stability, etc. That's why I'm not trying to take anything away from the overall FF3 effort ... there's a lot of changes outside the UI. But when you look at these UI changes, they're very basic. I'm hoping FF4 is more focused on seriously evolving the browser, and that means taking some chances and making some bold improvements to the shiny Fox machine.

<h2>And now ... The Firefox 4.0 Wishlist!</h2>

<h3>Shipping with Add-Ons</h3>

As I've said before, <a href="http://softwareas.com/flock-a-tribute-to-unusability-of-firefox-extensions">Firefox needs to ship with a proper suite of pre-installed extensions</a>. The "thin kernel model with optional extensions" is architecturally sound, and of course many applications now incorporate a plugin style architecture. The highly successful Linux and Apache web server projects are based on this model too. However, Mozilla misses a trick by shipping without key extensions. The attitude seems to be "if users want it, they can ^*@*!*#*$ install it themselves! The Mozilla people are in general extremely concerned with usability and the human factor, but in this case, the attitude reeks of Comic Book Guy geekery. Leaving out basic tab functionality, for example, yields unecessary advantages to Opera and Safari. Yes, it's available in TabMix if you care to download it, but if it's that important, then ship FF with TabMix!!!

There should be a standard distro with 5 or 6 popular plugins, all chosen for utility, simplicity, security, and compatibility with each other. This should be the one you get when you click the big, fat, super-easy-to-use, Download button (which I have always admired and has since been copied by many other websites). A bit deeper in the recesses of the Firefox distro site, you could also download the minimal edition as well as specialised editions. Alternatively, you might select your distro the first time you run a new Firefox profile. I could imagine a wizard that (a) asks you which distro (mapped to a set of add-ons), and then (b) lets you customise the list. This is much better than the current situation for creating a new profile, where you have to go and (re-)add all your typical add-ons manually, then restart.

It would be cool to see specialised editions for developers, students of different ages, gamers.

Apart from usability, this would be a boon for security, which is arguably Mozilla's primary concern and greatest source of pride when comparing Firefox to IE. Relieving most users from the need to install add-ons reduces the chance of a screw-up involving installation of a malicious plugin, or some unanticipated interaction between plugins that creates a hole. The default stack would be designed and tested for security, and any alerts involving an add-on in that stack will be highly visible.

<h3>Make it easier, much easier, to write Add-Ons</h3>

This was supposed to be an enhancement for FF3 iirc, but may have been dropped (?). Anyway, writing extensions in Firefox is a complicated business. You have to know XUL and deal with the whole packaging structure. It should be just as simple as writing Greasemonkey scripts IMO. I'd like to be able to say something like <tt>$("addressBar").style.backgroundColor = "red"</tt> for example. These things could be made possible with enhancements to Greasemonkey, but of course Greasemonkey isn't built in. What I'm looking for here must work with the raw version of Firefox. This will lead to a proliferation of cool new add-ons. It will also increase the risk of security violations as there will be more plugins around and it will be harder for Mozilla to vet them all, but relying on a difficult API to slow down add-on ... that's not the way to ensure security.


<h3>Installation of Add-Ons, Themes, Search</h3>

Installing search modules should work the same way as the new way to install add-ons and themes, ie all inside the client instead of bumping you to a website. Installing themes is half integrated but still requires you to go to a website. Even Add-Ons requires you to go to a website to explore fully. I think this should be unnecessary.

There is also confusion of terminology, with references to both "Add-Ons" and "Extensions". On the official add-on website, "Search" and "Themes" are combined with 10 other category of Add-On (Appearance, Bookmarks, etc.), whereas they are in fact special types of add-on. So in some cases, they are kept distinct, and in other cases, they are lumped together.

<h3>Improve Profile Management</h3>

I like the idea of profiles - as a developer, it would be nice to switch between a developer profile and a user profile. And also between multiple dummy user profiles while testing. But switching profiles requires a restart. Not only a restart, but you have to run Firefox with the "-p" flag, and the installer doesn't come with a launcher for profile-switch mode. For that reason, I bet most users probably don't even know this feature exists.

The simplest improvement would be for the installer to add a launcher for profile-switch mode to the Start menu (in windows at least), just like there is one for Safe Mode. Moreover, just integrate profile switching into the actual interface...just include a dropdown in the Advanced Preferences or add a new menu item somewhere which expands to show each profile ID. Easy! True, you'd still need a FF reboot. I don't see that constraint changing anytime soon ...

<h3>Tab-Mania! Sugoi yo ^o^</h3>

I wrote this up in <a href="http://softwareas.com/taking-browser-tabs-seriously">Taking Browser Tabs Seriously</a>. There's a ton that could and should be done to ease the multiple tab experience - notifying, searching, grouping, sorting, etc etc etc. This is HUGE! 'Nuff said, see the link for details.

<h3>Retain all viewed content (or at least index it for searching)</h3>

Come on, you know you want it! Instead of bookmarks, it's time to finally bite the bullet and let users search through every page they've visited (if not forever, then at least for the last X days). How many times do you have to search for something on Google that you've already seen before. The browser could take care of it. Just as Google search slams Yahoo taxonomies, so too does full-page history search obliterates bookmarking. I don't know how much capacity you'd need to do it, but I bet if you asked in 1994, "will we be able to do that in 2010, with 16 years = 1000x (ie 2^(16/1.5)) improvement in hardware stuff", you would answer a resounding yes. With the right optimisations, I'm fairly certain this is possible. BTW I realise you can effectively achieve all this now with Google, but there are a lot of reasons why it should be built into the browser (intranet and hidden content; privacy and corporate security concerns; possibility of offline browsing old content).

<h3>Improve history</h3>

With or without the previous enhancement, Firefox history has always been a bit wanting. For starters, search needs improvement - you should be able to search history the same way you search through a page. ie instead of filtering, it should just highlight matches and scroll to them. This way, you could see which other pages you were looking at around the same time. Sometimes, I'm searching for one term, but only because I know I was looking at another page at the same time, and I can't locate the other page via search. (Although I could do so if the previous enhancement was available!)

Search should also work without having to hit <tt>Enter</tt> - it should be updated on each keystroke just like page search.

Furthermore, it's excruciating trying to work out what time and date you viewed something. You get the "View by Date" which sorts by date, but doesn't let you search in this mode. And in any event, it still doesn't show you time of day. And if you view in other ways (by site or last/most visited), you don't get any time or date at all.

<h3>That Sidebar</h3>

I never get why there's only one sidebar when there are several possible contents (bookmarks, history, add-on-specific features). And it's also odd that you can only control that sidebar from the menu rather than the sidebar itself. You should be able to have multiple sidebars, or at least one accordian style sidebar containing all possible contents. Similar to the All-In-One Sidebar add-on.

I could imagine Firefox achieving flexible UI with an elastic docked window style UI like Eclipse (or indeed Firebug in some respects), but I think that would be too complicated for mainstream users.

<h3>Render Non-HTML Content</h3>

I realise a browser's fundamental job is to show web pages and it's rarely good when applications over-step their boundary, but in this case, I feel there is a case for putting in at least some effort on non-core activities. I'm talking about how Firefox (and every other mainstream browser) deals with non-HTML content. For example, this came up on <a href="http://twitter.com/mahemoff/statuses/837085942">Twitter today</a>, where my colleague mentioned <a href="http://twitter.com/tdroza/statuses/836825075">the problems we have viewing JSON in the browser</a>. It requires a download basically and then manually opening and viewing in your editor, and that's not very satisfactory. Even with XML, which <em>is</em> rendered by FF, how about some intelligent interpretation. If it's RSS or Atom, for example, provide a suitable default stylesheet explaining what it's good for and how to subscribe.

<h3>Better File System Navigation</h3>

When you visit a local directory using file://path-to-directory, what you are greeted with is an interface that hasn't changed since the mid '90s. Arguably, it's doing enough already, so why complicate it? But I think that exploring the filesystem is a rather useful feature for the browser, given its sovereign posture which means it could be used as the primary control centre for managing your local file system.

<a href="https://bugzilla.mozilla.org/show_bug.cgi?id=13607">It's also impossible to visit the root of your filesystem using file:///</a> on certain OS's, at least on my Mac. This is obviously fundamental behaviour that's missing, and the bug was logged in 1999! On my Mac, I also can't open up <tt>/Volumes/Macintosh HD</tt> due to the space. When I click on it from /Volumes, it changes to <tt>file:///Volumes/Macintosh%20HD</tt> and that URL breaks. Doh!

Just like Explorer or Finder, files should be shown in various possible formats - tabular (with sorting), thumbnail, etc. And it should use thumbnails to show file types.

<h3>Better Keyboard Binding Support</h3>

I like those programs like IntelliJ Idea which let you control keyboard bindings for pretty much anything, and also let you save and load configurations. Firefox should do the same. A lot of the shortcuts are hidden anyway and should be available somewhere in the interface, e.g. a keyboard preferences area.

<h3>Mouse Gestures</h3>

This was one of the awesome things about Opera when I first started using it and it made browsing fun and more subconscious, one step closer to the haptically brilliant Minority Report hand control scenario. I used it all the time, but on Firefox, the main add-on didn't work so well and I never got into it. Gestures should be built in so they are available to all users and available to all add-on developers. It would be even better if they were available to web apps as well, using some kind of whitelist if necessary (as I explained earlier wrt Growl).

<h3>Comment on the Coop</h3>

Incidentally, there is also <a href="http://wiki.mozilla.org/Labs/The_Coop">The Coop</a>. This was intended to ship with FF3, but dropped at some point. It's an attempt to embed social networking and stumbleupon-type functionality. To me, this is exactly the sort of thing that really is too far removed and should remain an optional add-on. It's actually tied to a single server run by Mozilla, which doesn't seem right for an open-source product. It might make more sense if it was generic platform/API, with the communication protocol published and the server software also open sourced.

<h2>Fin</h2>

Firefox is by far the best browser today, already has some great UI improvements from 2.0 days, and I am pleased that v3.0 is now more stable and performant than ever. Now I'm looking forward to usability improvements and looking forward to seeing other people's wishlists!
