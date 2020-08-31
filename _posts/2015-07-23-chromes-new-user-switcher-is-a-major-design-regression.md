---
id: 2153
title: 'Chrome&#8217;s new user switcher is a major design regression'
date: 2015-07-23T09:11:19+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2153
permalink: /chromes-new-user-switcher-is-a-major-design-regression/
categories:
  - Uncategorized
---
I rely on profile switching completely for day-to-day use. I have my personal Google account, Google apps account, a sandbox account for testing in clean-slate, a company account, support account, account for Google Play, account with read-only access to some servers which can be authorised to analytics tools, etc. Consultants often have one or more accounts per client.

The old "switching between different browsers" doesn't cut it, Chrome knew it when they introduced this feature, and with the latest update, it's become barely usable.

The new user navigation switcher:

<ul>
<li> Shows text labels instead of the instantly recognisable, customisable, graphical ones. Welcome to 1990, have a nice day.

<li> Requires an extra click to switch ("Switch profile") after hitting on the current profile name.

<li> Takes several seconds to open the switcher menu in its own dialog.

<li> After clicking twice to open the switcher and waiting around for it to paint, it only shows 8 profiles (what?!), only the first 8 in alphabetical order, and won't scroll for more. Turns out you have to manually expand it to see all profiles! Hidden core features ftw!

<li> The big compromise was to show the old menu if you click with the second mouse button. Well guess what, many of us don't have a second mouse button!

<li> The old menu can also be launched with ... a 2-finger tap on the trackpad. Yes, the only way to access this functionality is with an awkward 2-finger tap. It works 35% of the time for me, I'm trying to get some practice in so my average can hopefully get up to 50% (dream big). Keep in mind, this 2-finger tap is *the only way* I can access some of my profiles (those beyond the first 8).
</ul>

<p>Bottom line: Chrome had a great feature for years, which no other browser supports to this day. The architects of this feature have dropped the ball completely, given no explanation for these counter-intuitive design decisions, and hopefully Firefox or Edge will be there to pick up the slack.</p>

[All of the above issues are articulated in the bug tracker](https://code.google.com/p/chromium/issues/detail?id=403619) in very much the same way as the new design has no-one explaining the benefits. It's hard to see anything good about the new design.

It's not a case of wanting to stick to the old thing for the sake of not learning a new interface. It's a case of a serious design regression in every dimension, one that hasn't seen any rational justification from the designers.

Sometimes you can just tell when the designer doesn't use their own feature.