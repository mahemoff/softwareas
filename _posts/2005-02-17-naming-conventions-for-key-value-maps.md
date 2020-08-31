---
id: 58
title: Naming Conventions for Key-Value Maps
date: 2005-02-17T08:35:58+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=58
permalink: /naming-conventions-for-key-value-maps/
categories:
  - SoftwareDev
---
How do you name Maps? Maps of the key-value pair variety rather than the hip Google-enabled map of the USA.

There seems to be no convention. Even for individual programming languages, there seems to be no convention enshrined in the culture, although some languages naturally favour shorter names than others.

Letâ€™s say Iâ€™m mapping each captain to their respective team. There are several naming strategies:

* **values** as in *teams*. Succinct, but doesnâ€™t tell you what the keys represent. Itâ€™s usually not apparent from the declaration (e.g. Map) or initialisation (e.g. new HashMap()), so youâ€™d have to go and find code that uses it or read a comment. So it would be a particularly choice if used as a parameter for a published API.
* **mapFromKeysToValues** as in *mapFromCaptainsToTeams*. Says it all, if a bit verbose.
* **mapOfKeysToValues** as in *mapOfCaptainsToTeams*. Ditto.
* **keysToValues** as in *captainsToTeams*. More succinct, but the shorthand form belies that its a noun. So someone reading â€œprint(captainsToTeams)â€ will probably interpret it as â€œprint the map of captains to teams". Iâ€™d rather the structure be more clear at a glance.

I used â€œkeyToValuesâ€ for a long time, but Iâ€™ve recently switched to this:

* **valuesByKeys** as in teamsByCaptains. If youâ€™re going to include both key and value, this seems to read best. At a high level, you can read it as just â€œteams", so anything thatâ€™s performed on it is being performed on teams. The â€œâ€¦byCaptainsâ€ prefix reads as it should do: a less significant qualifier that follows the teams around to help someone understand the structure if they need to.

In all cases, Iâ€™ve assumed plural. Thereâ€™s certainly an argument to be made for singular form, as in captainToTeam, or any combination. I find plural works best in most contexts.

With template-style structures such as Java 1.5 offers, **values** might be the way to go. With a name like **teams**, you canâ€™t immediately tell the key type, but you can always locate the type in the declaration. Thatâ€™s different to the pre-1.5 situation, and dynamic languages, where you have to locate actual code. With the key type being part of the map type, simply **values** is probably the right trade-off. Unless the key type tells you little about the meaning of the key, such as String, in which case Iâ€™m still running with **keysToValues**.