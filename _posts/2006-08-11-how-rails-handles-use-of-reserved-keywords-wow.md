---
id: 339
title: How Rails Handles Use of Reserved Keywords, Wow!
date: 2006-08-11T15:58:31+00:00
author: admin
layout: post
guid: http://www.softwareas.com/how-rails-handles-use-of-reserved-keywords-wow
permalink: /how-rails-handles-use-of-reserved-keywords-wow/
dsq_thread_id:
  - "375573077"
categories:
  - SoftwareDev
tags:
  - HCI
  - Keywords
  - Rails
  - Ruby
---
I didn't ever expect to get excited about how a framework handles keywords, but Rails just impressed me big-time. When I tried to create a model named "Activity", Rails told me it was reserved and then <strong>came back with a list of thesaurus terms that might be used instead!</strong>. That's not just opinionated software, it's downright friendly! Most frameworks don't bother checking this sort of thing at all, let alone providing helpful "What To Do Now" instructions.

[html]
> ruby script/generate model activity

  The name 'Activity' is reserved by Ruby on Rails.
  Please choose an alternative and run this generator again.

  Suggestions:  

Sense 1
activity -- (any specific activity; "they avoided all recreational activity")
      => act, human action, human activity -- (something that people do or cause to happen)


Sense 2
action, activity, activeness -- (the state of being active; "his sphere of activity"; "he is out of action")
       => state -- (the way something is with respect to its main attributes; "the current state of knowledge"; "his state of health"; "in a weak financial state")


Sense 3
bodily process, body process, bodily function, activity -- (an organic process that takes place in the body; "respiratory activity")
       => organic process, biological process -- (a process occurring in living organisms)


Sense 4
activity -- ((chemistry) the capacity of a substance to take part in a chemical reaction; "catalytic activity")
       => capability, capacity -- (the susceptibility of something to a particular treatment; "the capability of a metal to be fused")


Sense 5
natural process, natural action, action, activity -- (a process existing in or produced by nature (rather than by the intent of human beings); "the action of natural forces"; "volcanic activity")
       => process -- (a sustained phenomenon or one marked by gradual changes through a series of states; "events now in process"; "the process of calcification begins later for boys than for girls")


Sense 6
activeness, activity -- (the trait of being active; moving or acting rapidly and energetically; "the level of activity declines with age")
       => trait -- (a distinguishing feature of your personal nature)
[/html]

It's interesting...the standard HCI advice for showing an error is to not only explain what's wrong, but <a href="http://www.softwareas.com/error-messages-wed-rather-not-see">how to fix it</a>. "Tell the user what happened, explain the consequences if itâ€™s not obvious, outline how to fix it, explain what to do if they canâ€™t fix it." Yet, how often do software tools, like compilers, give you anything more than a terse error message. Sure, it's important to be concise in some cases, but you could always offer an option, like --verbose, to actually provide a few insights.