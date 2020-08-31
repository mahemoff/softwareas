---
id: 565
title: Styling a Top Bar
date: 2009-08-06T01:32:04+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=562
permalink: /styling-a-top-bar/
dsq_thread_id:
  - "377213970"
categories:
  - HumansAndTech
  - SoftwareDev
---
<a href="http://digg.com/google.com">Digg Bar</a> launched with some controversy recently. It's iframe trapping all over again; sites like <a href="http://about.com">About</a> didn't make themselves too popular with this technique, and so it died down until recently. I think there are legitimate uses for the top bar though; certainly the Digg Bar is useful to at least those people who are currently logged into Digg.

In fact, the reaction in the past few months suggests that top bars are here to stay. There was an initial uproar, but it seems to have been accepted, and I think top bars will start to become a fixture of the web. Given the valuable tracking data that comes from it, I can imagine dominance of the top 40 pixels of the browser window will become a big deal too...and right now, the big GYM guys (Google/Yahoo/Microsoft) aren't doing it. Through development or acquisition, IMO that will change.

Users always trade off privacy against utility, and what can be an uproar about privacy concerns and google juice theft quickly dies down when people find value in a new feature. In this case, companies like Digg and StumbleUpon aren't producing top bars as part of a cynical get-rich-scheme; I believe competition is too fierce to resort to cheap tricks that will get users off-side. Instead, I believe they are genuinely aiming to win, adding awesome features to improve user experience first and foremost. The Google Juice and tracking data that comes with it is a gigantic dollop of icing on the cake and top bars therefore constitute another example of <a href="http://softwareas.com/designing-like-a-pollyanna-have-your-cake-and-eat-it-too">having your cake and eating it too</a>.

But this article is about web design, not web trends. An application of top bars I've been looking at recently is a "trails player" I've been building into <a href="http://scrumptious.tv">Scrumptious</a> lately. User creates <a href="http://softwareas.com/as-we-may-think-url-trails">a trail of websites</a> for someone to visit, and each of them shows up in a trail bar at the top of the page.

<a href="http://img.skitch.com/20090729-k5f8t8aawap8ysp8wjqdr84kc5.jpg"><img style="width:400px;" src="http://img.skitch.com/20090729-k5f8t8aawap8ysp8wjqdr84kc5.jpg" /></a>

To style this, I made like the web greats and peeked under the covers at a bunch of similar websites:

* <a href="http://digg.com/google.com">Digg Bar</a>
* <a href="http://burnurl.com/EFHRG7">BurnURL Bar</a>
* <a href="http://su.pr/A3qXoI">su.pr/StumbleUpon Bar</a>
* <a href="http://ow.ly/ixwK">Ow.ly Bar</a>

I've made a dead-simple bar to illustrate the concept.

<a href="http://jsbin.com/ayebe">View the top bar here</a>.

The canonical layout works like this:

[html]
  <head> 
    <link href="layout.css" rel="stylesheet" type="text/css" /> 
  </head> 
  <style> 
    body { overflow: hidden; } 
    iframe, div, body { margin: 0; padding: 0; } 
    #bar { position: absolute; top: 0; left: 0; width: 100%; height: 50px; 
              z-index: 100; 
              background: #ddf; border-bottom: 1px solid #888; } 
    #content { padding: 5px; } 
    iframe { margin-top: 50px; width: 100%; height: 100%; } 
  </style 
  <body> 
    <div id="bar"> 
      <div id="content">I am bar.</div> 
    </div> 
    <iframe src="http://yahoo.com"></iframe> 
  </body> 
</html>
[/html]

So the bar is absolute-positioned in the top-left, with width: 100% to span the entire width, and height set to whatever height you want for the bar. Make the iframe top margin match that height, and you're set.

Note that the bar shouldn't have any padding, otherwise it will add to the 100% width (padding isn't included in the width under standard CSS box model) . So if you want padding, put it inside an inner div, like #content above.

An interesting thing is that you can set the iframe's source, but you can't actually detect it, because of cross-domain security, under modern browsers. Which is unfortunate. The user might start clicking around inside the iframe, after you have set its initial source URL, and you won't actually know where they are at. Good for the user's privacy, but bad if you want to provide certain awesome features. e.g. Digg would probably like to show the number of Diggs on any page users click over to, and StumbleUpon would like to show votes as well as related pages. In Scrumptious, I'd like to provide a "trails recorder" that automatically scoops up pages you visit into a trail...but I'll have to achieve that with a browser extension.

And in all these cases, you probably want a "close bar" feature that would ideally work by setting document location to the iframe's source. ie you want something like <tt>document.location.href=$("iframe").attr("src");</tt>. But that fails because the right-hand side is null. The best you can do is set document.location.href to the last URL you pointed the iframe at.