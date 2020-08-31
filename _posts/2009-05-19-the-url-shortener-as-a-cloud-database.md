---
id: 537
title: The URL Shortener as a Cloud Database
date: 2009-05-19T21:22:23+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=534
permalink: /the-url-shortener-as-a-cloud-database/
dsq_thread_id:
  - "375574213"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Cloud DB
  - Experiment
  - Im8ge
  - Javascript
  - TinyURL
  - URL shorteners
  - Web
---
<h3>On URL Shorteners</h3>

URL shorteners are enjoying their 15 minutes of fame right now. They've been around since <a href="http://en.wikipedia.org/wiki/TinyURL">2002</a>, but became flavour of the month as soon as half of the planet decided to compress their messages into <a href="http://twitter.com">pithy 140-character microblogs</a>, and there is <a href="http://news.ycombinator.com/item?id=508132">money in it</a>, driving a massive amount of <a href="http://www.hongkiat.com/blog/url-shortening-services-the-ultimate-list/">new players</a> into the market, which will ultimately lead to a massive amount of <a href="http://joshua.schachter.org/2009/04/on-url-shorteners.html">URL shortener induced linkrot</a>. [Update Dec 2011 - I note that the URL shortener I used for a while, 3.ly, is now indeed linkrot :(.]

In passing, I will note the irony that <a href="http://kottke.org/08/02/single-serving-sites">long domain names</a> were the flavour of the month a year ago. Although, maybe it's not so ironic, since they enjoy a symbiotic relationship with the URL shorteners when you think about it.

Now, I recently realised that URL shorteners could be used as a form of cloud database. The URL is a form of data. And the interesting thing about this is that they form a cloud database that can be accessed from any Ajax app, because they (a) can be created anonymously; (b) <a href="http://code.google.com/p/bitly-api/wiki/ApiDocumentation">offer JSONP APIs</a>, in some cases (and with <a href="http://json-tinyurl.appspot.com/">third-party bootleg APIs</a> available in others); (c) allow you to store relatively long strings. Before you can say, "violation of Terms and Conditions", I will get to that later on.

<h3>Character Limits</h3>

On (c), just how long can these URLs be? I did a little digging - gave them some huge URLs to convert using just the homepage of each service. I chose the <a href="http://blog.tweetmeme.com/2009/03/23/shorten-it/">top services</a> from Tweetmeme's recent study, minus friendfeed's internal shortener, to come up with the four most popular services - tinyurl.com, bit.ly (my candidate for the first URL shortener to appear on the cover of Rolling Stone magazine, in case you ever doubted a URL shortener could be the in thing),  is.gd (the one I've been using since it was a wee thing spouting three-character shortcuts), and tweetburner aka trurl.nl.

I was expecting them all to truncate at around 2083 characters, the traditional limit for IE. Boy, was I wrong!

<img style="width: 400px;" src="http://img.skitch.com/20090519-cuq7pq4birxs1tb1rcaef44nna.jpg" />

I started playing around adding really long URLs, and playing a "Price Is Right" higher, higher, lower, higher game until I found out roughly the capacity of each.

<ul>
<li><strong>TinyURL</strong> <a href="http://preview.tinyurl.com/paam5w">65,536 characters</a> and probably more, but requests timed out; there isn't an explicit limit apparently</li>
<li><strong>Bit.ly</strong> <a href="">2000 characters</a>.</li>
<li><strong>Is.Gd</strong> <a href="http://is.gd/BpDQ">2000 characters</a>.</li>
<li><strong>Twurl.nl</strong> <a href=" http://twurl.nl/b48rgp">255 characters</a>.</li>
</ul>

Note that Bit.ly and Twurl.nl both give the impression they are storing more than their limits, i.e. they don't show an error message, but instead they silently truncate the URL. Is.Gd does the right thing by telling you what it's done. Although, the limits are weird - you would think they'd go for IE's 2083 character limit, or be all binary and go for 2048,  rather than cutting off at 2000. I guess 2000 is a simpler number to tell humans about.

So the most interesting one here is TinyURL. However, the actual underlying URL doesn't work for some reason - the most characters I found that would work was 8192. However, the entire URL is stored, as you can see <a href="http://preview.tinyurl.com/paam5w">at the preview page</a>.

<h3>A Legitimate, Related, Use: Shortening an Ajax Unique URL (with Fragment ID Reflecting App State)</h3>

The thought of using URL shorteners might sound crazy, useless, and a violation of terms, but it came to me for an entirely legitimate application, which is well within the T's and C's I believe. I'm creating <a href="http://caption.im8ge.com">a web app right now</a> (very incomplete) where the entire state is captured in the URL. (see <a href="http://ajaxpatterns.org/Unique_URL">Unique URL</a>. This saves me from having to set up any storage and (in some respects) makes life easier for users, who don't to manage yet another account, log in, etc etc. It certainly lowers the barriers for new users if they don't have to register in order to save things.

Saving the entire state in a URL can lead to a long URL. So with all the hype around URL shorteners, I figured why don't I just let the user save it to a short URL, if they do prefer a short URL for mailing or writing down, or memorising (since some of these services let you specify the key). And so I might choose to build into the app a little "get short URL for bookmarking and tweeting" button. (Funnily enough, I would have previously called it "bookmark this", but that would mislead users into thinking that the long URL on top isn't actually a valid bookmark. Now that everyone understands URL shorteners, I can be more explicit about the button's purpose.)

The short URL is effectively a holder of the entire state of this user's application. In fact, this seems like an entirely valid reason to use a URL shortener, so I doubt it's a violation of anyone's terms. Worth noting incidentally that there are plenty of free images where you can anonymously upload 100K or more, so I doubt a 10K URL is a big deal; and given that the service receives link love and some useful tracking data, it's probably just as valuable financially as an image sent to an image host.

<h3>A Pure Cloud Database</h3>

You can see where this is going. An extension to this thought is to simply treat the URL shorteners as cloud databases. As long as it looks like a valid URL, you could store whatever you like there. Turns out <a href="http://tinyurl.com/p944o6">you can even store an image</a> or a short MP3 as a data:// URI. I have no plans to do this, and I suppose it actually would be a violation of terms in this case, but it's an interesting idea.

And if the URL was too long, you could always use a linked list structure ---- break it up into several short URLs, with the last few characters of each source URL pointing the previous short URL. (it's backwards since you can then be sure what URL was allocated, and you would distribute the last URL in the series).

* http://tinyurl.com/mark3 end of the message mark2   (this is the URL you distribute)
* http://tinyurl.com/mark2 middle of the message mark1
* http://tinyurl.com/mark1 end of the message

There is actually prior art on this concept, I discovered - some anon poster recently created <a href="http://www.110mb.com/forum/storing-data-on-url-shortening-services-t45047.0.html">a proof-of-concept cloud DB</a>, with encryption to boot. There were no replies to that post and it seems to have gone unnoticed, which is unfortunate. So allow me to dig it out:

<blockquote>
<p>In almost obvious violation of their terms of service (maybe not entirely, they technically are urls, just with random data tacked onto it.) I've created a way to securely store arbitrarily length data on URL shortening services like tr.im, bit.ly, tinyurl, etc.

<p>You have to pass both the message and a key. The key is SHA-1'd and then the message is encryped with the key by AES-256. The message is split to 200 byte chunks and it loops through them. For each one, a special salt variable exists for no particular reason, is mixed with the key and a packet identifier number (part 0 = 0, part 1 = 1, so amazingly complex) and all of that is again SHA-1'd. It's trunkated to 14 digits. The part of the data is prepended with a pseudourl. and the url is passed to the url shortener API and the 14 digit string is used as the custom short URL. The last packet is appended with a special last-packet marker.

<p>http://jsbin.com/ixuda
</blockquote>

<h3>As We May Think</h3>

All this makes me think what kind of JSON-based cloud services there should be on the web, that would indeed be explicitly designed for this kind of purpose and be more suited to the purpose. I bet you could build something nice along those lines with <a href="http://tiddlyweb.org">TiddlyWeb</a> server.

The biggest restriction with all this is that the services are write-once. e.g. if you <a href="http://caption.im8ge.com">make a pretty poster</a>, tinyurl it, and send the link, you can never change the poster someone will see when they visit that link (because the link directly represents the composition of your poster, rather than being a pointer to the composition on the server).  So this heavily limits applicability of the concept anyway, but if users are willing to live with that restriction, it's a big benefit in terms of simplicity. You could also overcome the restriction using some of the newer URL shortening services that let you log in and maintain your shortcuts. But that would  (a) defeat the purpose of simplicity; (b) defeat the purpose of working in Ajax apps, since it would require privileged JSON calls, and privileged JSON calls are <a href="http://directwebremoting.org/blog/joe/2007/03/05/json_is_not_as_safe_as_people_think_it_is.html">wildly insecure</a>.