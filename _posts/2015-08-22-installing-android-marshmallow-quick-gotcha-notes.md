---
id: 2169
title: 'Installing Android Marshmallow &#8211; quick gotcha notes'
date: 2015-08-22T22:57:47+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2169
permalink: /installing-android-marshmallow-quick-gotcha-notes/
categories:
  - SoftwareDev
tags:
  - android
---
What the various guides often omit.

* Run android-sdk/tools/android and update platform-tools
* The oem unlock setting on phone kept reverting. But "fastboot oem unlock" fixed it.
* Ensure "adb devices" shows the device
* Ensure "Device State" on phone shows as UNLOCKED
* "cannot load 'system.img'" may happen because it requires several GB of free memory. So try chunking it: android-sdk/platform-tools/fastboot flash -S 512M system system.img
