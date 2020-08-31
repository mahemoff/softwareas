---
id: 1902
title: Revoking OAuth Tokens From Google, Twitter, etc
date: 2013-03-14T00:52:28+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1902
permalink: /revoking-oauth-tokens-from-google-twitter-etc/
categories:
  - SoftwareDev
---
The URLs below let you manage and revoke permissions you've given to third parties via Google, Twitter, Facebook, etc. It's not only useful for security, but also for testing while developing such tools. By deleting the connection, you can see what a user will see the first time they connect.

* <a href='https://accounts.google.com/IssuedAuthSubTokens'>Google App Permissions</a>
* <a href='http://twitter.com/settings/connections'>Twitter App Permissions</a>
* <a href='https://www.linkedin.com/secure/settings?userAgree=&goback=.aas'>LinkedIn App Permissions</a>
* <a href='https://www.dropbox.com/account#applications'>Dropbox App Permissions</a>

Mainly writing this because I keep searching for these things and don't have much luck (as I forgot about MyPermissions). Being personalised URLs, they don't show up in searches (which is a wasted opporunity, since they are all static and could have just been public placeholders). Hopefully this post will show up in the future when I search for "revoke OAuth Tokens". You can find links to more of these services on <a href='http://mypermissions.com'>MyPermissions</a>.