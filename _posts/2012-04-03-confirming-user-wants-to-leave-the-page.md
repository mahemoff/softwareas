---
id: 1613
title: Confirming User Wants to Leave the Page
date: 2012-04-03T22:11:39+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1613
permalink: /confirming-user-wants-to-leave-the-page/
categories:
  - SoftwareDev
---
So you have a user at your site and they wants to close your site or go elsewhere. In the past, the most likely way this would happen is clicking a link. But these days, almost all links are "target=_blank" popup links, and it's become so standard that it's almost rude not to. So that's not a scenario to consider. The scenario is where the user has closed your tab, perhaps inadvertently as part of a mass "close all tabs" or "quit browser" operation. Or they've typed in a new URL.

Most websites should in all sanity just concede at this point. Let the user be in charge and just move on from your site.

Some websites do have a legitimate need to do some work though. In the simplest case, they may just want to upload analytics. In more complex cases, they may want to save unsaved work. You can generally do that silently with an `onbeforeunload` handler.

And a scarce few websites may have a legitimate reason to confirm the user's action. I'd argue for a video or audio app like the one I'm building, that's what the user wants. If they're explicitly subjecting themselves to the audio stream coming out of your website, it's probably the only audio they're listening to at the time and there's a fair chance they don't want to close it. In which case, do this:

[code]
window.onbeforeunload =
  -> "You're currently playing. Are you sure you want to leave?"
  if playing()
[/code]

The point of interest here is it's "built-in". You just return a string. [You don't, and shouldn't, call <tt>confirm</tt>.](https://github.com/LeaVerou/dabblet/commit/a4124366cb6d6a372d9ee77adaaba3e59cb93c5a)

The other point is the `isplaying()` part! Breaking user expectations is not something to be done lightly.