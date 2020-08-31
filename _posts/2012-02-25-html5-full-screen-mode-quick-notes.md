---
id: 1522
title: 'HTML5 Full Screen Mode: Quick Notes'
date: 2012-02-25T13:34:06+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1522
permalink: /html5-full-screen-mode-quick-notes/
categories:
  - SoftwareDev
tags:
  - CSS3
  - fullscreen
  - html5
---
Just been playing with full-screen mode in Chrome, which lets any element become full-screen (not just video, as I think it was envisioned in earlier days). Wanting to get this working nicely on mobile devices, I've also done some experimenting with graceful degradation / progressive enhancement as it applies to full-screen mode.

### Basic Version

Although you <i>can</i> full-screen any element, I decided to full-screen the entire body, then use [a kind of classy HTML](http://softwareas.com/classy-html-a-speculative-design-pattern-about-classes-and-composition) to show what needs to be shown in full-screen mode. (Mainly because I'm using a component that wasn't immediately working when I full-screened it directly.)

I'm using a full-screen toggle element, here's the CoffeeScript:

[code]
  $('#fullScreen').click (ev) ->
    if document.webkitIsFullScreen then document.webkitCancelFullScreen() else document.body.webkitRequestFullScreen()
[/code]

Note that you cancel on document (that's the only thing you can cancel on), but you set it on any element (though you actually can't set it on document!). Also, note that the user could manually hit escape to exit, so don't think that you're always in control of full-screen state. Hence the <tt>webkitIsFullScreen</tt> check instead of trying to maintain state in a flag variable.

Following the Classy HTML pattern, the CSS here is based on a new pseudo-selector which gets applied to the body element. We can easily decide what to include in full-screen mode. In this case, as the SCSS below shows, I've simply elevated the map element above everything else, but knock yourself out.

[code]
:-webkit-full-screen {
  #map {
    position: absolute;
    z-index: 2000;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}
[/code]

And no, it's not just for Webkit...go check out [MDN's full-screen docs](https://developer.mozilla.org/en/DOM/Using_full-screen_mode) for more info.

### Graceful Degradation Version

But what if there's no full screen mode? We can still make that full-screen toggle useful by expanding content to max out the browser screen, even though the browser itself can't switch into full screen mode. So here's another crack at it, where we use the true Classy HTML pattern, i.e. instead of styling according to the built-in full-screen pseudoselector, we make our own "fullScreen" class. If the document is in either :-webkit-full-screen or "fullScreen" state, we'll max out the important content.

[code]
  fullScreenEnabled = (typeof(document.webkitCancelFullScreen)!='undefined')
  $('#fullScreen').click (ev) ->
    if fullScreenEnabled
      if $('body:-webkit-full-screen').length
        document.webkitCancelFullScreen()
      else
        document.body.webkitRequestFullScreen()·
    else # oh well, at least we can big up the content inside the browser
      console.log('full not enabled')
      if $('body').hasClass('fullScreen')
        $('body').removeClass('fullScreen')
      else
        $('body').addClass('fullScreen')
[/code]

The style is exactly the same as before, just with two selectors involved. Something like this, in theory:

[code]
:-webkit-full-screen,.fullScreen {
  #map {
    position: absolute;
    z-index: 2000;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}
[/code]

But in practice, for some hair-pulling reason, non-webkit browsers will ignore that entire rule, so I had to duplicate it:

[code]
:-webkit-full-screen {
  #map {
    position: absolute;
    z-index: 2000;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}

/* As DRY as mud...but I found this duplication required */ 
.fullScreen {
  #map {
    position: absolute;
    z-index: 2000;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}
[/code]

Now the full-screen toggle works for all browsers. But full-screen enabled browsers get the nice bonus of busing out of the browser tab and taking up the entire desktop.

(Again, I confess, this is me messing around with webKit only for now. The graceful degradation stuff does work with Firefox of course, though it could do more than just that. I haven't used full-screen on Firefox simply because there are other components not working on Firefox, and this post is based on practical experience. It's well-supported on both Firefox though as well as Chrome.)