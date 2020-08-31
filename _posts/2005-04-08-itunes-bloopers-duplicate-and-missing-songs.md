---
id: 91
title: 'ITunes Bloopers: Duplicate and Missing Songs'
date: 2005-04-08T07:31:59+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=91
permalink: /itunes-bloopers-duplicate-and-missing-songs/
categories:
  - HumansAndTech
---
ITunes has two serious usability bloopers in its handling of the music database.

<h4>Duplicate songs</h4>

It's very possible you'll end up with the same song twice. Perhaps you forgot you'd already imported it. I've been having problems with IPodder pushing songs into ITunes , so I've been manually dragging results of a Recent Files query, leading to some duplicates in the overlapping dates.

Until recently, ITunes did nothing. **Now, I've just installed 4.7 after being seduced by [Apple's promotion of its "Duplicate Songs" feature](http://www.apple.com/itunes/import.html)**:

<small>
> **Eliminate Duplicate Tracks Easily**
> Ever import a â€œGreatest Hitsâ€ album only to find that you already have one or more of the songs in your iTunes music library? Now we offer a handy way to resolve that little complication. iTunes 4.7 makes it easy to find multiple copies of the same song. Just choose â€œFind duplicatesâ€ from the Edit menu, and iTunes will display all the duplicate songs in your music library, making it very easy for you to decide which of the duplicates â€” if any â€” youâ€™d like to delete.
</small>

<b>Easily??? Nope. Find Duplicates really means what it says: it shows all the versions of the same file.</b> So you're left with all the twins an triplets in the same list. As in:

* DSC 1 - Adam Curry
* DSC 1 - Adam Curry
* ITC 1 - Gillmor Gang
* ITC 1 - Gillmor Gang

You get the idea. How do you "eliminate" those tracks??? The "handy way" Apple offers is to take a shovel and get to work, because you're going to be deleting them one-by-one. According to [this IPodLounge](http://www.ipodlounge.com/articles_more.php?id=6162_0_8_0_C), that's a feature and not a bug:

<small>
> Apple's feature was designed more to prevent mistakes than to annoy you. It's much safer to delete songs one by one, and really be sure you want to delete them, rather than delete a whole bunch of songs and regret it later. Other programs may work better or worse, depending on your needs. 
</small>

That's only speculation, but if it's really true, that's just wrong: the computer is much better at performing a tedious operation like that than the human. Design it right, test it thoroughly, and it will work fine. It's a trivial algorithm after all. In contrast, ask a user to manually delete duplicates and there will be boredom at best, tears at worst. Remember there's not always two items; sometimes there will be three or four. So you can't just go into a trance of "delete, yes, down, down". You have to watch the whole thing. BORING!

**More to the point, duplicates should never be allowed in the first place.** The best designs prevent errors, rather than worrying how to recover from them. That's the logic behind disabling buttons that just don't make sense at that time. When you import a file, it should prevent it from being included if the location already exists. Not rocket science.

<h4>Missing Files</h4>
**A related problem occurs when files go missing.** After some unspecified time, ITunes notices and offers "?" icons. Thanks, better than nothing, but you know these are meant to be some pretty big databases ... could you let me filter on those anomalous files, so I can work out what to do with them. Just treat "underlying file exists" as another attribute like Date Added, and then it can be incorporated easily into the View Options.

<h4>"But You're Trampling on its Model of Simplicity"</h4>

... I hear you cry. Actually, duplicate files can happen to even the most basic of users, and there's no threat to ITunes' simple model by preventing them in the first place. Missing files is a slightly more "power user" function, since it implies you've been playing with the file system. Still, ITunes works by synchronising with the underlying system, so it's still in order to provide some support for dealing with this problem. A simple filter would do nicely.