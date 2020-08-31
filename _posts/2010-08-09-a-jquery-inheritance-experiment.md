---
id: 938
title: A jQuery Inheritance Experiment
date: 2010-08-09T01:18:54+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=938
permalink: /a-jquery-inheritance-experiment/
dsq_thread_id:
  - "375184941"
categories:
  - SoftwareDev
tags:
  - Javascript
  - JQuery
---
I <a href="http://softwareas.com/tag/jquery">like jQuery a lot</a>, but I often find myself <a href="http://softwareas.com/automagic-event-registration">re-doing my way of OO</a> and inheritance each time I start a new app. And so, I just did it again of course.

I was starting to write a lame HTML5 game, where you have "AlienModels" (of the MVC, not Star Trek, variety), and each with their own "AlienView". When an AlienModel enter()s, its view will detect a "enter" event and show the alien entering the scene. Certain types of aliens will fly in, certain aliens will fade in, and so on. I started creating an AlienView abstraction, but I figured this is something jQuery can do for me. An AlienView might simply be a jQuery selector. However, this is where jQuery reaches its limits, as I want to call $("someAlienView").enter(50,50), and to have the alien's entry towards co-ordinate (50,50) animated, but animated differently depending on what kind of alien it is.

So I created a framework to do this. <a href="http://jsdo.it/mahemoff/yvOL/fullscreen">Code and Demo here.</a>

The usage is this:
[html]
<div class="shy guy">shy</div>
<div class="fly guy">fly</div>
[/html]

[javascript]

    $(".shy").define({
      disappear: function() { $(this).slideUp(); }
    });

    $(".fly").define({
      disappear: function() { 
        $(this).fadeOut().fadeIn().fadeOut().fadeIn().fadeOut().fadeIn()
               .animate({top: -200 }).hide();
      }
    });

    $(".guy").disappear();
[/javascript]

When we call $(".guy").disappear(), what happens depends on whether this is a ".shy" or a ".fly". This is basic polymorphism, which jQuery lacks. The $.fn.define() plugin I wrote (see the code in that example) shoehorns it in, but maybe that's not a good idea...I'm making jQuery into something it's not. So on IRC someone pointed me to <a href="http://ryanflorence.com/object-oriented-jquery-with-mootools-pigs-take-flight/">this MooTools-jQuery article</a>. I need to read that article. I also need to get into MooTools, which I think may be more appropriate for this kind of thing, with its unashamed use of prototype (afaict). In general, my urge for more OO and scalable architecture tells me I need to look further afield than jQuery. But syntactic sugar trumps all, so I'll only go elsewhere if it doesn't smell of enterprisey, false sense of security, <a href="http://www.youtube.com/watch?v=5kj5ApnhPAE">public static void</a>ness.

Incidentally $.fn.define() could go further than I currently have it; it would be possible to set up an inheritance chain, where you could define $(".guy").disappear() explicitly, so that if an element matched ".guy"  but not ".shy" or ".fly", it would follow the ".guy" rule. (But not the other way round.) I probably won't though.

Incidentally (2), thanks @agektmr for telling me about <a href="http://jsdo.it">jsdo.it</a>, a mostly-Japanese Javascript pastebin similar toas <a href="http://jsbin.com">jsBin</a> and <a href="http://jsFiddle.net">jsFiddle</a>.