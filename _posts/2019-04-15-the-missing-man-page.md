---
id: 2296
title: The Missing Man Page
date: 2019-04-15T09:00:23+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2296
permalink: /the-missing-man-page/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";N;s:10:"author_url";N;s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";N;s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";N;}'
categories:
  - SoftwareDev
---
If only man pages were as good as the first Google result, [I idly tweeted](https://twitter.com/mahemoff/status/1117355866225893377) while trying to coerce curl into post a form [1]. The ensuing conversation led me to think about exactly what is missing in man pages.

When I say "the first Google result", I'm *not* talking about StackOverflow in this case. We can all agree Stack has mystic levels of ability to answer the question your man page can't, or not in under 15 minutes anyway. I'm thinking more about reference material; what exactly is wrong with man pages? And why do the newer alternatives, such as [tldr pages](https://tldr.sh/), fall short of replacing them?

My primary thesis is that man pages are an artifact of a long-bygone era, where the only electonics docs available were those that shipped with the tool itself. There was no web and no convenient way to collaborate at scale.

With man pages being tethered to the tool itself, this means that the docs are maintained by the tool maintainer, who is not always best equipped to write documentation. This is probably better nowadays, for tools using Github/Gitlab etc, where others can come in and improve docs, however it was suggested on Twitter that some maintainers may block valuable contributions. There's also the well-known lack of funding for generic tools, which means even if project maintainers wanted someone to create better docs, there's no funding for it.

Compare that to the incentive to create a gret web reference, where a company like W3CSchools can rake in $millions as the top Google result for just about any search. It's a competitive marketplace.

In fact, this is a problem with all official docs. Even tools which do have viable commercial models still have poor online documentation in many cases. Take a look at MySQL's documentation on creating a new user. User management is one of the main pain point of friction in the system, and this is their official documentation for it. You land from Google and you're greeted by this giant complicated regex, wrapped in a jungle of navigation links! Is it any wonder DigitalOcean pays a writer to [make a sane third-party reference guide](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql) in an SEO play that could end up outranking the official doc? 

<a href="http://softwareas.com/wp-content/uploads/2019/04/Selection_755.png"><img src="http://softwareas.com/wp-content/uploads/2019/04/Selection_755-300x193.png" alt="" width="300" height="193" class="alignnone size-medium wp-image-2297" /></a>

This illustrates that the people creating the tool aren't necessarily the people best placed to document it? That doesn't have to be the case of course. These days, companies understand the value of developer experience and some, like Stripe, produce [outstanding docs](https://stripe.com/docs). However, that doesn't translate to your run-of-the-mill Unix staple.

This is where tools like tldr and cheat can make a difference. They are separate from the tool itself, anyone can contribute. However, their explicit goal is to be concise, which means they are not an apples-to-apples alternative because man pages are designed to be exhaustive.

My biggest gripe with the format of man pages is that they try to act too much like textbooks, which is entirely inappropriate when you are trying to get some quick info to solve a problem. Again, it's an artifact of a time before the web, where the most convenient way to ship around an essay about the tool was ship it with the tool. Here, for example, is what I see with `man find`.

<a href="http://softwareas.com/wp-content/uploads/2019/04/Selection_756.png"><img src="http://softwareas.com/wp-content/uploads/2019/04/Selection_756-269x300.png" alt="" width="269" height="300" class="alignnone size-medium wp-image-2298" /></a>

You'd never see this level of caveats and hand-waving in a Digital Ocean sponsored post on how to find files on your file system. At the least, it would be buried at the bottom of the doc, with the important stuff, like a simple annotated example first.

So what I'd like to see is something exhaustive, but with options grouped logically, not alphabetically, and each one of them illustrated by examples. Man pages don't do this and nor do tldr or cheat.

Making better documentation is a lot of hard work, which is why StackExchange abandoned its [Documentation experiment](https://meta.stackoverflow.com/questions/354217/sunsetting-documentation). So I don't see the problem being solved anytime soon, and it's why I'll continue using a web search for now. 

### Footnotes

1. I'd normally be using the more inuitive [HTTPie](https://httpie.org/) for this, but sometimes you need to share it with people who are used to curl.