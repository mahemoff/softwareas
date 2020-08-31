---
id: 125
title: 'Don&#8217;t Force Users to Qualify Lookups'
date: 2005-05-14T20:51:39+00:00
author: admin
layout: post
guid: http://www.softwareas.com/dont-force-users-to-qualify-lookups
permalink: /dont-force-users-to-qualify-lookups/
dsq_thread_id:
  - "525312861"
  - "525312861"
categories:
  - HumansAndTech
---
An unfortunate  feature of many lookup services is their insistence on having the user type something, then qualify what sort of thing they're looking up. Or, to qualify by typing in a different form field. Examples:

* [The Aussie White Pages Lookup](http://www.whitepages.com.au/wp/busSearch.jhtml) requires you to indicate the state (from eight choices) you're searching for.
* Most [foreign language dictionaries](http://www.spanishdict.com/) require you to say which direction you're translating in, even though you might end up switching frequently. [The Yahoo translater](http://education.yahoo.com/reference/dict_en_es/) shows how it should be done - a single form where you can enter a word in English or Spanish.

Qualifying might be useful as an option to help reduce results, but shouldn't be mandatory. In many cases, there is only one answer *without* qualifying, so why force the user to specify a qualifier when it's not needed?

On the bright side, Google, for instance, will offer News results when you perform a regular search. Theer were rumours a while ago it was occasionally providing images too. I think this is  a good move, and they could go further. As long as it's clear which are the results you specifically searched for, why not show results for several categories. Likewise, you rarely have to qualify searches on Amazon. You just search for a term like "Pulp Fiction" without wasting any time telling Amazon what kind of product you're looking for.

Now, you might say performance improves when users qualify things - you have an extra constraint to your "WHERE" clause. It's true, but let's face it: Do you really think that's the reason this design faux pas occurs? Experience and the fact that it probably wouldn't make much difference would suggest the design has simply not been taken that seriously. Even if performance were considered, the only relevant measure is how quickly users can perform their tasks, and this would probably improve overall even if the CPU was doing more work. And there would be less incorrect queries if users weren't forced to specify the information.

This problem occurs due to tech-driven, rather than user-driven design. Instead of looking at the user's task, the designers have focused only on the database schema. A pat on the head is in order from the DBA, while the user hits the "X" icon.