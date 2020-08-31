---
id: 446
title: World timezone data
date: 2008-05-14T13:28:18+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=443
permalink: /world-timezone-data/
dsq_thread_id:
  - "375573704"
categories:
  - SoftwareDev
tags:
  - Ajax
  - clock
  - Javascript
  - time
  - timezone
---
Writing a multi-timezone clock gadget, I found myself needing to convert timezones in Javascript. This is one uncharted area in Ajax/Javascript - unfortunately, there is no timezone library to my knowledge. Unfortunately, there's no public JSON service to tell you what time it is right now in Tokyo either. I could create one without too much difficulty, but I'm aiming to build a self-contained gadget, which means I want it all in Javascript.

Back to first principles, <a href="http://en.wikipedia.org/wiki/Zoneinfo">ZoneInfo</a> is incredibly thorough, but that makes it difficult to use for a single gadget. There is a <a href="http://en.wikipedia.org/wiki/List_of_time_zones">wikipedia list too</a>, but not easily parsed. (If web 3.0 is all about the semantic web, then wikipedia will hopefully become a better home for structured data too.) I then found <a href="http://citytimezones.info/cms/index.htm">"City Time Zones"</a> which is a user-generated, wiki-style, approach. The problem is it doesn't handle daylight savings, but it will do for now - the user will simply get a checkbox to say if it's daylight savings or not. Yeah it's a really ordinary solution, but the only one I can manage if I'm to build the gadget in a day or so.

I extracted from the ZoneInfo a simple list you might find useful. The first iteration is sorted by timezone and I've junked geo and other info, so you just have the timezone names, the offset, and major locations.

<blockquote>
Tonga Standard Time,+13:00 Nuku'alofa<br/>

Kamchatka Standard Time,+12:00 Kamchatka<br/>

Fiji Standard Time,+12:00 Fiji, Marshall Is.<br/>

New Zealand Standard Time,+12:00 Auckland, Wellington<br/>

Norfolk Island Standard Time,+11:30 Norfolk Island<br/>

Central Pacific Standard Time,+11:00 Solomon Is., New Caledonia<br/>

Magadan Standard Time,+11:00 Magadan<br/>

Vladivostok Standard Time,+10:00 Vladivostok<br/>

Tasmania Standard Time,+10:00 Hobart<br/>

West Pacific Standard Time,+10:00 Guam, Port Moresby<br/>

AUS Eastern Standard Time,+10:00 Canberra, Melbourne, Sydney<br/>

E. Australia Standard Time,+10:00 Brisbane<br/>

AUS Central Standard Time,+09:30 Darwin<br/>

Cen. Australia Standard Time,+09:30 Adelaide<br/>

Yakutsk Standard Time,+09:00 Yakutsk<br/>

Korea Standard Time,+09:00 Seoul<br/>

Tokyo Standard Time,+09:00 Osaka, Sapporo, Tokyo<br/>

Ulaanbaatar Standard Time,+08:00 Ulaanbaatar<br/>

Taipei Standard Time,+08:00 Taipei<br/>

W. Australia Standard Time,+08:00 Perth<br/>

Singapore Standard Time,+08:00 Kuala Lumpur, Singapore<br/>

North Asia East Standard Time,+08:00 Irkutsk<br/>

China Standard Time,+08:00 Beijing, Chongqing, Hong Kong, Urumqi<br/>

North Asia Standard Time,+07:00 Krasnoyarsk<br/>

SE Asia Standard Time,+07:00 Bangkok, Hanoi, Jakarta<br/>

Myanmar Standard Time,+06:30 Rangoon<br/>

Sri Lanka Standard Time,+06:00 Sri Jayawardenepura<br/>

Central Asia Standard Time,+06:00 Astana, Dhaka<br/>

N. Central Asia Standard Time,+06:00 Almaty, Novosibirsk<br/>

Nepal Standard Time,+05:45 Kathmandu<br/>

India Standard Time,+05:30 Chennai, Kolkata, Mumbai, New Delhi<br/>

West Asia Standard Time,+05:00 Islamabad, Karachi, Tashkent<br/>

Ekaterinburg Standard Time,+05:00 Ekaterinburg<br/>

Afghanistan Standard Time,+04:30 Kabul<br/>

Caucasus Standard Time,+04:00 Yerevan<br/>

Tbilisi Standard Time,+04:00 Tbilisi<br/>

Baku Standard Time,+04:00 Baku<br/>

Arabian Standard Time,+04:00 Abu Dhabi, Muscat<br/>

Iran Standard Time,+03:30 Tehran<br/>

E. Africa Standard Time,+03:00 Nairobi<br/>

Russian Standard Time,+03:00 Moscow, St. Petersburg, Volgograd<br/>

Arab Standard Time,+03:00 Kuwait, Riyadh<br/>

Arabic Standard Time,+03:00 Baghdad<br/>

Turkey Standard Time,+02:00 Turkey<br/>

Israel Standard Time,+02:00 Tel Aviv, Jerusalem<br/>

Syria Standard Time,+02:00 Syria<br/>

Jordan Standard Time,+02:00 Jordan<br/>

FLE Standard Time,+02:00 Helsinki, Kyiv, Riga, Sofia, Tallinn, Vilnius<br/>

South Africa Standard Time,+02:00 Harare, Pretoria<br/>

Egypt Standard Time,+02:00 Cairo<br/>

E. Europe Standard Time,+02:00 Bucharest<br/>

Lebanon Standard Time,+02:00 Beirut<br/>

GTB Standard Time,+02:00 Athens, Beirut, Istanbul, Minsk<br/>

W. Central Africa Standard Time,+01:00 West Central Africa<br/>

Central European Standard Time,+01:00 Sarajevo, Skopje, Warsaw, Zagreb<br/>

Namibia Standard Time,+01:00 Namibia<br/>

Romance Standard Time,+01:00 Brussels, Copenhagen, Madrid, Paris<br/>

Central Europe Standard Time,+01:00 Belgrade, Bratislava, Budapest, Ljubljana,

Prague<br/>

W. Europe Standard Time,+01:00 Amsterdam, Berlin, Bern, Rome, Stockholm,

Vienna<br/>

GMT Standard Time,+0:00 Dublin, Edinburgh, Lisbon, London<br/>

Greenwich Standard Time,+0:00 Casablanca, Monrovia<br/>

Azores Standard Time,-01:00 Azores<br/>

Cape Verde Standard Time,-01:00 Cape Verde Is.<br/>

Mid-Atlantic Standard Time,-02:00 Mid-Atlantic<br/>

Argentina Standard Time,-03:00 Argentina<br/>

E. South America Standard Time,-03:00 Brasilia<br/>

SA Eastern Standard Time,-03:00 Georgetown, South America Eastern Time<br/>

Greenland Standard Time,-03:00 Greenland<br/>

St Pierre and Miquelon Standard Time,-03:00 St Pierre and Miquelon<br/>

Uruguay Standard Time,-03:00 Uruguay<br/>

Newfoundland Standard Time,-03:30 Newfoundland<br/>

Atlantic Standard Time,-04:00 Atlantic Time (Canada)<br/>

Falkland Islands Standard Time,-04:00 Falkland Islands<br/>

SA Western Standard Time,-04:00 La Paz<br/>

Paraguay Standard Time,-04:00 Paraguay<br/>

Pacific SA Standard Time,-04:00 Santiago<br/>

Venezuela Standard Time,-04:30 Venezuela<br/>

SA Pacific Standard Time,-05:00 Bogota, Lima, Quito<br/>

Cuba Standard Time,-05:00 Cuba Standard Time<br/>

Eastern Standard Time,-05:00 Eastern Time (US & Canada)<br/>

US Eastern Standard Time,-05:00 Indiana (East)<br/>

Central America Standard Time,-06:00 Central America<br/>

Central Standard Time,-06:00 Central Time (US & Canada)<br/>

Mexico Standard Time,-06:00 Guadalajara, Mexico City, Monterrey<br/>

Guatemala Standard Time,-06:00 Guatemala<br/>

Honduras Standard Time,-06:00 Honduras<br/>

Canada Central Standard Time,-06:00 Saskatchewan<br/>

US Mountain Standard Time,-07:00 Arizona<br/>

Mexico Standard Time 2,-07:00 Chihuahua, La Paz, Mazatlan<br/>

Mountain Standard Time,-07:00 Mountain Time (US & Canada)<br/>

Pacific Standard Time,-08:00 Pacific Time (US & Canada); Tijuana<br/>

Alaskan Standard Time,-09:00 Alaska<br/>

Hawaii-Aleutian Standard Time,-10:00 Adak<br/>

Hawaiian Standard Time,-10:00 Hawaii<br/>

Samoa Standard Time,-11:00 Midway Island, Samoa<br/>

Dateline Standard Time,-12:00 International Date Line West<br/>


</blockquote>

Yes, Tonga is 13 hours of UTC and 25 hours ahead of those little-known places that are UTC-12. In fact, Kiribati Istland (not shown here) is +14 so a day and 2 hours ahead of the others. This wasn't meant to be easy.

Anyway, I simplified the list further to:
<blockquote>
+13:00 Tonga<br/>

+12:00 Auckland, Wellington, Fiji, Marshall Is., Kamchatka<br/>

+11:30 Norfolk Island<br/>

+11:00 Solomon Is., New Caledonia, Magadan<br/>

+10:00 Canberra, Melbourne, Sydney, Brisbane, Hobart, Guam, Port Moresby<br/>

+09:30 Darwin, Adelaide<br/>

+09:00 Seoul, Yakutsk, Osaka, Sapporo, Tokyo<br/>

+08:00 Taipei, Ulaanbaatar, Perth, Kuala Lumpur, Singapore, Irkutsk, Beijing,

Chongqing, Hong Kong, Urumqi<br/>

+07:00 Bangkok, Hanoi, Jakarta, Krasnoyarsk<br/>

+06:30 Rangoon<br/>

+06:00 Sri Jayawardenepura, Astana, Dhaka, Almaty, Novosibirsk<br/>

+05:45 Kathmandu<br/>

+05:30 Chennai, Kolkata, Mumbai, New Delhi<br/>

+05:00 Islamabad, Karachi, Tashkent, Ekaterinburg<br/>

+04:30 Kabul<br/>

+04:00 Tbilisi, Yerevan, Baku, Abu Dhabi, Muscat<br/>

+03:30 Tehran<br/>

+03:00 Moscow, St. Petersburg, Volgograd, Nairobi, Kuwait, Riyadh, Baghdad<br/>

+02:00 Turkey, Tel Aviv, Jerusalem, Syria, Jordan, Helsinki, Kyiv, Riga, Sofia, Tallinn, Vilnius, Harare, Cairo, Bucharest, Beirut, Athens, Beirut, Istanbul, Minsk<br/>
<br/>

+01:00 Sarajevo, Skopje, Warsaw, Zagreb, Brussels, Copenhagen, Madrid, Paris, Belgrade, Bratislava, Budapest, Ljubljana, Prague, Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna, West Central Africa, Namibia<br/>

+0:00 Dublin, Edinburgh, Lisbon, London, Casablanca, Monrovia<br/>

-01:00 Azores, Cape Verde Is.<br/>

-02:00 Mid-Atlantic<br/>

-03:00 Argentina, Brasilia, Georgetown, South America Eastern Time, Greenland, 
Uruguay<br/>

-03:30 Newfoundland<br/>

-04:00 Atlantic Time (Canada), Falkland Islands, La Paz, Paraguay,

Santiago<br/>

-04:30 Venezuela<br/>

-05:00 Eastern Time (US & Canada), Bogota, Lima, Quito, Havana<br/>

-06:00 Central Time (US & Canada), Central America, Guadalajara, Mexico City,

Monterrey, Guatemala, Honduras, Saskatchewan<br/>

-07:00 Mountain Time (US & Canada), Arizona, Chihuahua, La Paz, Mazatlan<br/>

-08:00 Pacific Time (US & Canada), Tijuana<br/>

-09:00 Alaska<br/>

-10:00 Hawaii, Adak<br/>

-11:00 Midway Island, Samoa<br/>

-12:00 International Date Line West<br/>

</blockquote>

<a href="http://softwareas.com/raw-timezone-list">Also available in cut-and-paste form</a>
