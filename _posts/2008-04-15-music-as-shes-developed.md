---
id: 439
title: 'Music As She&#8217;s Developed'
date: 2008-04-15T07:44:28+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=436
permalink: /music-as-shes-developed/
dsq_thread_id:
  - "375409355"
categories:
  - General
  - HumansAndTech
  - SoftwareDev
tags:
  - Announcement
  - Last.FM
  - Mashup
  - Music
  - Navel-Gazing
  - Widgets
---
I made a little music mashup you might enjoy using.

<h3>A Little Music</h3>

As I was playing around with the new layout of this blog, I added a <a href="http://last.fm">Last.FM</a> widget to the sidebar. It looks like this:

<style type="text/css">table.lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8 td {margin:0 !important;padding:0 !important;border:0 !important;}table.lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8 tr.lfmHead a:hover {background:url(http://cdn.last.fm/widgets/images/en/header/radio/mini_red.png) no-repeat 0 0 !important;}table.lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8 tr.lfmEmbed object {float:left;}table.lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8 tr.lfmFoot td.lfmConfig a:hover {background:url(http://cdn.last.fm/widgets/images/en/footer/red.png) no-repeat 0px 0 !important;;}table.lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8 tr.lfmFoot td.lfmView a:hover {background:url(http://cdn.last.fm/widgets/images/en/footer/red.png) no-repeat -85px 0 !important;}table.lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8 tr.lfmFoot td.lfmPopup a:hover {background:url(http://cdn.last.fm/widgets/images/en/footer/red.png) no-repeat -159px 0 !important;}</style>
<table class="lfmWidgetradio_eef448421daa7cdb759397e5f8ea67f8" cellpadding="0" cellspacing="0" border="0" style="width:110px;"><tr class="lfmHead"><td><a title="Music tagged trance " href="http://www.last.fm/listen/globaltags/trance" target="_blank" style="display:block;overflow:hidden;height:20px;width:110px;background:url(http://cdn.last.fm/widgets/images/en/header/radio/mini_red.png) no-repeat 0 -20px;text-decoration:none;border:0;"></a></td></tr><tr class="lfmEmbed"><td><object type="application/x-shockwave-flash" data="http://cdn.last.fm/widgets/radio/25.swf" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,0,0" width="110" height="140" > <param name="movie" value="http://cdn.last.fm/widgets/radio/25.swf" /> <param name="flashvars" value="lfmMode=radio&amp;radioURL=globaltags%2Ftrance&amp;title=Music+tagged+trance+&amp;theme=red&amp;lang=en&amp;widget_id=radio_eef448421daa7cdb759397e5f8ea67f8" /> <param name="bgcolor" value="d01f3c" /> <param name="quality" value="high" /> <param name="allowScriptAccess" value="always" /> <param name="allowNetworking" value="all" /> </object></td></tr><tr class="lfmFoot"><td style="background:url(http://cdn.last.fm/widgets/images/footer_bg/red.png) repeat-x 0 0;text-align:right;"><table cellspacing="0" cellpadding="0" border="0" style="width:110px;"><tr><td class="lfmConfig"><a href="http://www.last.fm/widgets/?url=globaltags%2Ftrance&amp;colour=red&amp;size=mini&amp;autostart=0&amp;from=code&amp;widget=radio" title="Get your own widget" target="_blank" style="display:block;overflow:hidden;width:85px;height:20px;float:right;background:url(http://cdn.last.fm/widgets/images/en/footer/red.png) no-repeat 0px -20px;text-decoration:none;border:0;"></a></td><td class="lfmPopup"style="width:25px;"><a href="http://www.last.fm/widgets/popup/?url=globaltags%2Ftrance&amp;colour=red&amp;size=mini&amp;autostart=0&amp;from=code&amp;widget=radio&amp;resize=1" title="Load this radio in a pop up" target="_blank" style="display:block;overflow:hidden;width:25px;height:20px;background:url(http://cdn.last.fm/widgets/images/en/footer/red.png) no-repeat -159px -20px;text-decoration:none;border:0;" onclick="window.open(this.href + '&amp;resize=0','lfm_popup','height=240,width=160,resizable=yes,scrollbars=yes'); return false;"></a></td></tr></table></td></tr></table>

(May not render if you're reading this from a feed reader.)

Great. Now I can listen to trance from the blog. Trance is good for coding. So that's ace. But I couldn't stop there, could I?

<h3>Widgets, Widgets, Everywhere!</h3>

I made <a href="http://softwareas.com/my-music">this page</a> with 30+ gadgets in all sorts of genres. This is good for those times when I'm not coding and want to listen to something else. Being in the cloud, it means I can easily listen to whatever I feel like when I'm in an internet cafe or the such like.  So even more ace.

<a href="http://softwareas.com/my-music"><img src="http://img292.imageshack.us/img292/6863/blogmusicem1.png"></a>

<h3>Make Your Own Jukebox</h3>

In the spirit of sharing, you can easily make a page containing your own favourite music. The URL for the default music page resolves to something with a ridiculously long list of genres:
[html]
http://softwareas.com/music?tags=trance,ambient,meditation,triphop,funk,randb,rap,hiphop,metalrap,latin,salsa,reggaeton,rock,pop,retro,alternative,metal,punk,aussie,britpop,europop,world,bhangra,arabic,70s,80s,90s,house,techno,electro,acid,garage,psychedelic,jazz,swing,lindyhop,classical,instrumental,orchestral
[/html]
... which means you can hack the URL and make your own jukebox with your own genres and bookmark it and it will work and live on in the cloud and you too will be able to listen to your favourite music anywhere you go.

For example, you might be a more passionate fan of contemporary Japanese music than myself, in which case you would concoct the following URL and save it to your delicious bookmark manager to enjoy many years of musical gratification:

<a href="http://softwareas.com/music?tags=j-ska,j-pop,j-punk,j-hop,j-rap,anime">http://softwareas.com/music?tags=j-ska,j-pop,j-punk,j-hop,j-rap,anime</a>

<h3>Add A Player on the Fly</h3>

One other feature is that you can add a new player on the fly. This again is great for travelling around  as it will let me easily listen to any genre I care for without even having to edit the URL.

<a href="http://softwareas.com/my-music"><img src="http://img246.imageshack.us/img246/7753/blogmusicaddhw3.png"></a>

(Unamusing trivia: I actually caused a bug at first by using "gray" as the colour name here. I'm used to working with American spelling for programming of course, but then last.fm is a UK company and the name you want is actually British spelling, i.e. "grey".)

<h3>Obligatory Wishlist I'll Not Really Get Around to Implementing But it's Cathartic to Braindump it Anyway</h3>

If I was going to do more work on this, I would:

* Make it into a widget-like portal which lets you add/remove/layout etc and save settings within a hackable URL (using <a href="http://ajaxpatterns.org/Unique_URL">Unique URL</a>. You could argue the whole thing is useless as you could achieve the same thing in iGoogle/Shindig, but sometimes a specialised interface, tucked neatly inside a separate tab, works best.
* Provide more flexibility on layout
* Add support for bands, not just tags
* Run it on a separate page without the blog layout
* Keep the loldog

<a href="http://softwareas.com/my-music"><img src="http://img337.imageshack.us/img337/3082/dogmusictb4.png"/></a>