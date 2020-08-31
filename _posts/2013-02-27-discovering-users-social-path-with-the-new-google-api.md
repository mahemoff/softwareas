---
id: 1891
title: 'Discovering Users&#8217; Social Path with the New Google+ API'
date: 2013-02-27T01:17:22+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1891
permalink: /discovering-users-social-path-with-the-new-google-api/
categories:
  - General
tags:
  - API
  - Google
  - GooglePlus
  - OAuth
  - oauth2
---
Google announced a slew of identity and social updates today, most excitingly, the ability to browse users' social paths. This happens after similar services recently blocking some folks from doing so, which tells you Google gave it due consideration and is committed to supporting this feature indefinitely.

Here's how the authentication looks:

<img src='http://i.imgur.com/40I4saN.png' />

Now there's a whole set of widgets and JavaScript APIs, but I was interested in the regular scenario for apps already using the "traditional" OAuth 2 dance. After <a href='https://plus.google.com/106413090159067280619/posts/Ry7qkifQmGP'>asking</a> on the G+ APIs community, I was able to get this running and I'll explain how below.

Step 1. Visit the API doc: <a href='https://developers.google.com/+/api/latest/people/list'>https://developers.google.com/+/api/latest/people/list</a>

Step 2. Scroll to the interactive part below and turn on OAuth 2.0 on the top-right switch.

<img src='http://i.imgur.com/djGezx3.png' />

Step 3. To the default scope, add a new one: <tt>https://www.googleapis.com/auth/plus.login</tt>. That's the magic scope that lets your app pull in social graphs.

<img src='http://i.imgur.com/KNVgpaj.png' />

Step 4. For userID, enter "me". For collection, enter "visible". (This collection property, representing circles/people the user can identify to the app, only has that one value at present.)

<img src='http://i.imgur.com/tE8agYI.png' />

Step 5. Now hit execute and (as a test user) you'll see the dialog shown at the top of this article. Then hit accept.

Step 6. I got a confirmation dialog saying "Clicking Confirm will let Google APIs Explorer know who is in your circles (but not the circle names). This includes some circles that are not public on your profile." which is surprising as I believe circles are always private (for now), so I guess users will always see that. Accept it.

Step 7. The JSON response will now be shown below the form. It includes a top-level field called "items", which is the list of your (the authenticated user's) G+ people. If the list is too long, there will also be a "nextPageToken" field so the app can page through the list.

So that's an overview of the new G+ social API. It's a straightforward OAuth implementation and should be easy for anyone with a Google login to adopt. I've been looking forward to adding this functionality on [Player FM](http://player.fm) so people can see what their friends are listening to ... I think it's a nice model where users can choose how much of their social graph they share with any app.