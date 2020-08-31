---
id: 443
title: FireEagle Developer Event
date: 2008-04-30T23:18:44+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=440
permalink: /fireeagle-developer-event/
dsq_thread_id:
  - "381973274"
categories:
  - General
  - SoftwareDev
tags:
  - Ajax
  - Brickworks
  - FireEagle
  - Geo
  - OAuth
  - Yahoo
---
<a href="http://fireeagle.yahoo.com"><img src='http://img139.imageshack.us/img139/4127/fireeaglefc0.png' alt='FireEagle' class='alignnone' /></a>

I discovered at last minute a developer event on <a href="http://fireeagle.yahoo.com">Yahoo! FireEagle</a> at Covent Garden tonight and decided to rush down there. FireEagle is pretty intriguing as the first serious attempt at an OAuth API (though Google Contacts now qualifies too). For me, that was the main draw; but the actual service it offers is also compelling.

<h2>What's FireEagle?</h2>

Location based services have been hyped for years. By now, you should be walking around and receiving reviews of local restaurants on your phone, browsing nearby tourist attractions, and seeing which of your friends is in your vicinity. However, it hasn't caught on. The main reason is stovepipes and walled gardens. Your mobile provider <i>might</i> have an API available, but probably restricted access to a very limited set of developers. A mix of privacy and commercial concerns have rendered this whole area practically useless.

Enter the eagle. FireEagle completely opens up this area, by offering a model that is flexible and open, but without compromising user privacy. It's an API that essentially tracks one thing: Where in the world are all FireEagle users?

In other words, the FireEagle API allows any client to update a user's location and any client to retrieve a user's location. Of course, the user must consent to all this activity, and that's where OAuth comes in - as a way for users to say, for example, "I trust app abc to update my location and app xyz to read my location". So FireEagle detaches location providers from location consumers, opening up an entire ecosystem.

What kind of clients act as location updaters? You might think it's all automated stuff, like mobile devices and IP numbers, but actually many updaters are manual. Here's a sample:

* Mobile phone app. Anyone with the right access details could write a mobile phone app to use cell tower information, built-in GPS, or any other cues, to update location as the user moves around. This is the no-brainer example of an automatic mobile updater.
* Twitter. When you tweet with "L: london", a twitter monitor app could notice that and notify FireEagle. (As with all cases below, you must have authorised the monitor app to do that.) This example illustrates that users aren't always passive lemmings walking around with a mobile updater app in their pocket. It may be that location data is only ever updated when a user proactively tweets their location.
* A client that watches you adding geotagged photos to Flickr, and assumes you are in the last location you uploaded.
* Specialised tracker device. Devices based on GPS (e.g. <a href="http://international.findmespot.com/">SPOT</a>) could easily be made to update FireEagle with their location.
* Car app. Based on GPS, a car's location could be tracked using FireEagle. (The car, not the driver.)
* Travel card. (My example.) Theoretically, your travel card could update FireEagle location as you move around. Same for transponder devices in cars.
* Many, many, more examples.

What kind of clients act as location consumers?

* Find nearby friends, tourist attractions, pubs, etc.
* Find currency rate (since you know what country they're in)
* Phrases in the local lingo or an online dictionary
* Location based games
* Many, many, more examples

Some clients may act as both updater and consumer.

<h2>Privacy</h2>

The other thing FireEagle gets right is great concern for privacy - users can give out as much or as little data as they like, and they can stop the service at any time. The first way this happens is with OAuth, which lets you manage which services can perform what actions. You can start and stop this at any time. In the future, there will be a simple client to let you log in from your mobile and control all this. In particular, you will probably be able to suspend all tracking at any time.

Additionally, you can apparently set granularity, so you could expose just a general area, e.g. whiiich city or country you're in, instead of a particular co-ordinate.

In the future, you will probably be able to authorise a client just for a certain time, e.g. during a conference, after which it can no longer access your data.

At some point, historical data may become available. The team said if this happens, they will allow users to delete and edit their past data.

In summary, the team has been very careful to ensure users have complete control over their own data,

<h2>Very Raw Notes from Presentation</h2>

Tom Coates is talking about FireEagle.

FireEagle is the old CS classic: a layer of intermediation - between location
identification systems and location consumer systems. As a user, I can tell
FireEagle where I am and any permissioned app can make use of that data.

London is about the most frequent location for fireeagle

What would your existing/past apps look like if they had location services
available?

e.g. Navizon

e.g. ZoneTag

e.g. Firebot - Make it your twitter friend and direct message your location to
it.

e.g. BrightKite - cf dodgeball

e.g. Rummble

e.g. Plazes - determines your location via wifi. Then shows where you are on
map, people around you, etc etc. And updates FireEagle

WikiNear - ~1M geo-tagged articles in wikipedia. Wikinear exploits that data -
as you're walking around, shows you the closest POIs that are in wikipedia.

Lightpole

Outside.In

Fireball - where your friends are

Fire Widgets - weather where you are, nearby Flickr photos

Moveable Type

Facebook "friends on fire" app - shows where your friends are and updates your
Facebook status

Could be great...

Spot - specialised comms/phone device for backpackers, aid workers, etc.
~100pound for device, 100pound a year and keeps updating your location everyï¿½
ten minutes. Doesn't integrate yet but great example if it did

Ambient Orb - e.g. changes colour as you move away

Nabaztag

Geotagging all user generated content - cinema listings, local traffic, local
TV stations, nearby  friends, weather forecast, local exchange rates, public
holidays, windspeed. A lot of this is on wikipedia thanks to geotagging.

Friends and family widgets. e.g. where they are in the world, what time it is,
weather, etc. (A gadget for each person.)

Last.FM - On cracked iphone, can get mobile scrobbler on iphone. What if it
recorded where you were, then you could see which songs people play in
particular areas. Cool!

Pacmanhattan - Lots and lots of game ideas (idea: scavenger hunt! reminds me of
geocaching)

(later mention: geocoding animals, e.g. track migration)

-----------------

Later on, expecting it to track historical data. (and since it will be
user-modifiable which means you could back-track your entire life! (or someone
elses eg fake shaekspeare))

http://tinyurl.com/5gtj92

http://tinyurl.com/3uklhl

----------------------------------

<h3>Building an APP</h3>

(http://fireeagle.yahoo.net/developer/documentation/getting_started)

1 - Get API key
2 - User authorises your app
3 - Make API calls to Fire Eagle
Outside.In -ï¿½

Who's within an area

Each consumer key and secret identifies an application using Fire Eagle.

User Authorises ....

<b>There are three models and the difference is purely to do with differences in
(app triggering web page) and (web page triggering app).</b>
Web: Can trigger in both directions
Mobile: Can't trigger in either direction (maybe, but can't assume it)
Desktop: App can trigger web page, web page can't trigger app

Web App model: Request token

<b>I asked which model was used for widgets. Answer: Desktop.</b> (Makes sense, with
current technology. Web model would cause redirection from container. Later on,
Opensocial will have oauth built in.)

<h2>Core Concepts</h2>

Note: social graph (user and friends) is beyond scope

location - point or bounding box
location hierarchy - set of locations

Exposed RESTfully:

* user() - duh
* lookup() - provide location string and choose from list of resolutions (which "london"??)
* update() - duh. call it and it "moves you"
* within() - ?
* recent() - "map of soho and everyone in there" OR "last 100 updates from my users"

walking through http://github.com/mojodna/fireeagle-tutorial/tree/master/ruby

Will probably support xmpp/Jabber too - more appropriate than HTTP for this