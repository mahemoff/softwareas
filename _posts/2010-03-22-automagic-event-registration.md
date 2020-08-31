---
id: 829
title: Automagic Event Registration
date: 2010-03-22T10:43:33+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=829
permalink: /automagic-event-registration/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574690"
categories:
  - SoftwareDev
tags:
  - Ajax Patterns
  - Dependency Injection
  - Javascript
  - JQuery
---
Further to <a href="http://mini.softwareas.com/playing-with-jquery-custom-events-good-tip-fr">last night's post on custom events</a>, I've set things up now to use "magic event registration". It's a little like the <a href="http://static.springsource.org/spring/docs/2.5.6/reference/beans.html#beans-factory-autowire">auto-wiring facility of a dependency injection container</a>. It's quite simple really - the app's initialisation sequence does this:

* Register all components that might listen to something.
* Register all events they might listen to.
* For each listener method among the components, automatically bind the event to it.

In code:
[javascript]
  var components = [siteFrame, singleTrial, trialController, statsZone, tableView, analysis, rawView, graphView];
  var eventTypes = ["trialCreate", "trialUpdate", "trialSuspend", "trialRun", "trialComplete"];
  $.each(components, function(i,component) {
    $.each(eventTypes, function(i,eventType) {
      var handler = component[eventType];
      if (handler) $(document).bind(eventType, handler);
    });
  })
[/javascript]

A component looks like:

[javascript]
statsZone = {
  trialCreate: function(e, trial) {
    ...
  },
  trialUpdate: function(e, trial) {
    ...
  }
}
[/javascript]

And elsewhere in the code, the events it listens to get triggered through the normal jQuery custom events mechanism:

[javascript]
  $(document).trigger("trialUpdate", trial);
[/javascript]

Part of this is based on what I said last night, which is (a) I'm keeping things simple - hence everything happens at startup and all the instances are singleton classes; (b) consequently, events are global, rather than being attached to any particular component.

Stepping back, what were the alternatives to this design:

* Components register themselves as listeners - this would be the purist OO answer, i.e. keeping objects autonomous. A perfectly cromulent solution, but a little more redundancy than it needs to be. If objects really do have consistently named listener methods, it's just as easy to handle registration automagically.

* The initialisation routine manually wires up components to events. It has a certain Python-like "explicit" feel to it, but again is quite pointless if we can instead do it automagically.

So where does the automagic model fall down? If we are doing things dynamically, it would get more complicated and would, for example, require objects to register upon their creation. So I think that's still okay. Another problem could be if a single method was listening to more than one event type, since this technique assumes it's one-to-one from event type to methods. But that's okay too - I actually had this problem and it was simply solved by getting both handlers to delegate to a third, common, handler:

[javascript]
var trialController = {
  trialCompleteOrCreate: function() {
    ...
  }
}
trialController.trialCreate = trialController.trialComplete = trialController.trialCompleteOrCreate;
[/javascript]

I realised while working on TiddlySpace there's a lot to be said for dependency injection style patterns in Javascript, and it's not happening yet.