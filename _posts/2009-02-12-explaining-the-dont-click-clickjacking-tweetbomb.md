---
id: 522
title: 'Explaining the &#8220;Don&#8217;t Click&#8221; Clickjacking Tweetbomb'
date: 2009-02-12T19:38:00+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=519
permalink: /explaining-the-dont-click-clickjacking-tweetbomb/
dsq_thread_id:
  - "375574157"
categories:
  - SoftwareDev
tags:
  - Clickjacking
  - Security
  - Twitter
  - Web
---
I just noticed some of my Twitter friends posting the following mysterious message:

"Don't Click: http://tinyurl.com/amgzs6"

It turns out this is a Tweetbomb. If you go to that link and click on the button below, you end up tweeting the same thing:

<img src="http://img.skitch.com/20090212-q26u5i49megqwrappy9qsmrcjn.jpg" />

... thus all your friends see it and some of them click on it and re-post it, and so on, thus propagating the message across the entire Twittersphere.

TinyURL shut down the redirect quickly and <a href="http://blog.twitter.com/2009/02/clickjacking-blocked.html">Twitter has responded</a>, but the same attack could arise unless measures are taken. Of which, more later.

So how does this hack work?

The hack is an example of <a href="http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9115818&source=NLT_SEC&nlid=38"><strong>clickjacking</strong></a>. (I've heard the term a lot, but only understood its meaning after the investigation of this tweetbomb described here.)

Firstly, it's using an iframe to embed Twitter.com on the page. The iframe is essentially invisible, due to the CSS structure...more on that in a moment. But first, looking at the source of the iframe, we spot our mysterious message:

<pre>
&lt;iframe src="http://twitter.com/home?status=Don't Click: http://tinyurl.com/amgzs6" scrolling="no"&gt;&lt;/iframe&gt;
</pre>

Well, I didn't know about this before, but it turns out you can set an initial value for the status field by passing in a "status" parameter on the URL. So here, it's setting the status to out mysterious message. You can try it yourself by visiting <a href="http://twitter.com/home?status=Don't Click: http://tinyurl.com/amgzs6">http://twitter.com/home?status=Don't Click: http://tinyurl.com/amgzs6</a>. (It's safe to do so - nothing will get submitted, honest!) For the lazy and untrusting ;), what you'll see at that URL is something like this, assuming you're logged in to Twitter:

<img style="width: 400px;" src="http://img.skitch.com/20090212-d3ntuiij9rfj5f8sh1t5yebt14.jpg" />

However, their job is not done yet, because they also have to trick you into clicking the "update" button. This is where more cunning comes into play. Check out the CSS for the iframe - containing your Twitter.com page - and the fake button contained on this trickster website:

[css]
		iframe {
			position: absolute;
			width: 550px;
			height: 228px;
			top: -170px;
			left: -400px;
			z-index: 2;
			opacity: 0;
			filter: alpha(opacity=0);
		}
		button {
			position: absolute;
			top: 10px;
			left: 10px;
			z-index: 1;
			width: 120px;
		}
[/css]

And the elements:

<pre>
	
&lt;iframe src="http://twitter.com/home?status=Don't Click: http://tinyurl.com/amgzs6" scrolling="no"&gt;&lt;/iframe&gt;

&lt;button&gt;Don't Click&lt;/button&gt;
</pre>

We can see from the CSS z-indexes, the iframe is on top of the button. And we can see from the iframe's opacity that it is completely invisible. <strong>Hmmm...so it's on top, but completely invisible. If there was a button there, you wouldn't be able to see it, but you <b>would</b> still be able to click on it.</strong> This is where the layout comes in (position, width, height, top, left). The iframe is positioned just right so the the (invisible) update button appears in the top-right of the web page at (10,10), right where the fake button is. So the Update button is directly above the fake button but invisible. <strong>The website shows a fake button and tempts you to click on it, but clicking on it causes the real Twitter button - inside the iframe - to fire.</strong> Thanks to the URL status hack, you have just submitted their planted message. And of course, you couldn't see the message, because the iframe is hidden and because that part of the iframe is not present anyway due to the negative left and top settings. There is also some filler text on the trickster page, below the fake button - I guess this is in case some browsers expand the iframe height if nothing else is on the page.

<a href="http://img.skitch.com/20090212-jp26n8uwkhqnsfxt87drnyx6tu.jpg"><img src="http://img.skitch.com/20090212-jp26n8uwkhqnsfxt87drnyx6tu.jpg" style="width:400px; "/></a>

The main way Twitter can prevent this kind of attack is to use the old <a href=""http://stackoverflow.com/questions/369498/how-to-prevent-iframe-from-redirecting-top-level-window>"bust the iframe" idiom</a>. As I explained in <a href="http://softwareas.com/cross-domain-communication-with-iframes ">Cross-Domain Communication with IFrames</a>, it's possible for an iframe to access the URL of its container, and actually re-set that value. Thus the common pattern:

[javascript]
if (top.location.href != self.location.href)
     top.location.href = self.location.href;
[/javascript]

If Twitter had that code on its web page, whenever it was loaded inside an iframe, the user would see the entire page clear and refresh to become the Twitter URL that was in the iframe. I actually think it's a shame they would have to resort to something like that, because there are valid uses for iframes, as <a href="http://webwait.com">WebWait</a> demonstrates. Any site that uses this pattern cannot bathe in the warm glow of WebWait :). But I can see why sites need to take this measure. (Update: Twitter has updated their code to bust out of the cache, just after I posted this!)
