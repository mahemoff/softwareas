---
id: 2284
title: Black Mirror Bandersnatch Spoilers
date: 2018-12-29T14:53:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2284
permalink: /black-mirror-bandersnatch-spoilers/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"107a3a697256";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:41:"https://medium.com/@mahemoff/107a3a697256";}'
categories:
  - Uncategorized
---
Here's just a few random thoughts on <a href="https://www.netflix.com/title/80988062">Black Mirror Bandersnatch</a>, which came out yesterday. I'd have posted these as a few lazy tweets, but didn't want to post spoilers there.

Haven't watched it yet? Congratulations, you have a life. But go watch it anyway. Binge the first four seasons beforehand if you haven't seen them yet. Also worth it.

Thoughts with some very mild spoilers ahead:

<ul>
    <li>"Choose Your Own Adventure" previously moved from book form to interactive game form, as depicted in Bandersnatch. Netflix's experiment takes it another step to streaming form, which is interesting because there's no way to look at the code and figure out every path. It also means they could change the path dynamically, e.g. introduce an easter egg for just one day.</li>
    <li>But what about narrative, in a world where viewer decide the story? This is a popular trope in interactive storytelling, the tension between the producer guiding the story and the viewer feeling free to make decisions. The entire story of Bandersnatch addresses that tension better than anyone could express in a linear sentence. Free will in this medium is an illusion.</li>
    <li>Netflix's long term goal likely involves VR and personalization, i.e. personalized videos similar to the recent bubble of books where $child_name is the star. It's not hard to see how gaming and movies eventually converge. A degree of interaction is an important step towards this future.and</li>
    <li>Netflix's short term goal likely see this as a popular move for some kids' content. I've noticed Netflix also has Jeaopardy in its catalogue and it's a no-brainer for the platform to be used for interactive TV game shows, as has long been done with cable remotes, but better.</li>
</ul>

A few technical observations:

<ul>
    <li>The number input (for the safe) shows this is not just going to be a simple 2-way choice mechanism. I'm guessing they have set up a protocol to support input of any unicode string.</li>
    <li><del>I noticed the episode doesn't work on my Shield running recent (probably latest?) Android TV OS</del> (Update: it works now, a day later, it must have required an app update.) Netflix has a lot of clients and it will be a big effort to implement - and evolve - this protocol ubiquitiously. They'll also have to think about different input constraints, e.g. typing on TV might support voice input.</li>
    <li>I also noticed the episode isn't possible to download, and at one point saw it buffering after making a decision (on a bad network). The app probably pre-emptively downloads a minute or two of both decision paths so it can continue seamlessly after each decision. It would also probably hang on to the unchosen path in the event it's needed later. Overall, there are some very interesting computer science and network topography problems for anyone wanting to optimise a system like this.</li>
</ul>

<a href="https://www.netflix.com/title/80988062"><img class="alignnone size-medium wp-image-2285" src="https://i.imgur.com/4r2tpMV.jpg" alt="Netflix Bandersnatch" width="400" height="240" /></a>
