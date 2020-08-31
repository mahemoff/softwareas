---
id: 515
title: 'TiddlyWiki &#8211; Showing a Help Message Related to the Tiddler'
date: 2009-02-03T16:59:46+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=512
permalink: /tiddlywiki-showing-a-help-message-related-to-the-tiddler/
dsq_thread_id:
  - "389135532"
categories:
  - SoftwareDev
---
A useful #tiddlywiki conversation with <a href="http://about.unamesa.org/Saq+Imtiaz ">Saq</a>.

[16:39] mahemoff: here is an idea i had for my app - just wondering if anyone else has seen this ...<br>
[16:40] mahemoff: i'm thinking of using a field to provide some instructions for certain tiddlers <br>
[16:40] mahemoff: and updating ViewTemplate to render the field to certain users (this is a tiddlyweb app)

[16:41] saqimtiaz: mahemoff: look at the annotations macro

[16:41] mahemoff: ie those with permissions to change the tiddlers<br>
[16:41] mahemoff: ok looking...

[16:41] saqimtiaz: mahemoff: its used by the core to add instructions when editing certain shadow tiddlers<br>
[16:41] saqimtiaz: mahemoff: it stores the text in a config.*something var instead of fields though<br>
[16:41] saqimtiaz: but otherwise the same idea<br>
[16:41] saqimtiaz: mahemoff: a good way to see it in action is to edit the StyleSheet tiddler

[16:41] mahemoff: nice! sounds exactly the kind of thing. i might need to mod it though to show in view mode for certain users

[16:42] saqimtiaz: mahemoff: I think that might be as simple as putting the macro call in the view template

[16:43] mahemoff: yes, but as it's conditional i'll probably need to create another macro that invokes the tiddlyweb macro<br>
[16:44] mahemoff: or some hijack-fu

[16:44] saqimtiaz: mahemoff: right. You may just find that its simpler to write a small macro to do it from scratch rather than building on top of this.<br>
[16:45] saqimtiaz: mahemoff: if you're not familiar with it already, the easiest way to call one macro from inside another is usually the invokeMacro function.

[16:46] mahemoff: ah didn't actually know that, i did it before manually, thanks.

[16:46] saqimtiaz: mahemoff: another thought. HideWhen plugin from mptw.tiddlyspot.com can be used to add conditional components to templates like the ViewTemplate<br>
[16:46] saqimtiaz: so a combination of say annotation macro or HideWhen macro might do the trick.