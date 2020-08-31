---
id: 391
title: 'How to share your Mac desktop (OSX 10.4 &#8211; Tiger)'
date: 2007-07-24T07:00:23+00:00
author: admin
layout: post
guid: http://www.softwareas.com/how-to-share-your-mac-desktop-osx-104-tiger
permalink: /how-to-share-your-mac-desktop-osx-104-tiger/
dsq_thread_id:
  - "375208977"
categories:
  - SoftwareDev
tags:
  - Apple
  - Mac
  - OSX
  - VNC
---
I had my first remote desktop sharing experience on a Mac yesterday. I needed to run a demo on my Mac for a remote user, and it turned out to be not all too challenging, once I worked out what software was required. All of it free and painless to set up for both parties.

Here's how you do it. "You" are the one sharing your desktop, i.e. showing what's on your screen to someone else on the net. "The Viewer" is the someone else viewing your desktop.

<h4>Enable Remote Desktop Sharing on your Mac</h4>

Fortunately, this is free and built into Tiger - you just need to be enable it.

* System Preferences | Sharing | Apple Remote Desktop. Tick this option.
* Click on Access Privileges
* Tick "Observe", "Show when being observed", "Guests may request permission to control screen", and "VNC viewers may control screen with password"
* Enter the password next to the last of these options, e.g. we'll assume it's "easy2guess".

<h4>Set Up Port Forwarding on your Mac</h4>

You're probably running this behind your router, so log into your router and <a href="http://docs.info.apple.com/article.html?artnum=106847">forward incoming TCP port 5900</a> to your PC.

Port forwarding is a whole topic in itself and if you don't know anything about it, you'll need to <a href="http://portforward.com/routers.htm">read up</a>. Very briefly, it means that when a request comes into your router which sits at the front of your LAN, the router knows which PC to send it to. To set up port forwarding on your router, you'll need to know: (a) how to log into your router and change port forwarding options; (b) the local IP number of the machine you want to share - run ipconfig or ifconfig and look for a number like 192.168.something or 10.0.something, or look at your router's output; (c) the port number - I just told you that. (It's usually configured as a range, so just use 5900-5900.)

Well done. Your machine is now ready to be shared.

<h4>Viewer Installs a VNC Client</h4>


<img src="http://picupper.com/2007/07/23/chickenvnc.jpg" style="float: right; margin: 10px; width:80px; height:80px;"/>

The Viewer will need to install a VNC client. If they're using a Mac, may I suggest <a href="http://sourceforge.net/projects/cotvnc/">Chicken of the VNC</a>, a fine open-source product whose merit extends beyond its moniker. Worked for me anyway. <a href="http://www.nonstopmac.com/2006/02/chicken_of_the_vnc.htm">Detailed chicken review here</a>. As with most reviews though, it doesn't say much about the big picture and what happens on the server, hence the article you're reading.

<h4>Pass on your External IP Number to Viewer</h4>

Just prior to connecting, pass your external IP number to the Viewer by phone or email. Fastest way to determine it is to visit <a href="http://whatsmyip.org/">WhatsMyIP.org</a>. It's also in your router app somewhere. 

<h4>Viewer Connects to Your Machine</h4>

The Viewer runs the VNC client and enters your IP number (with chicken, run Open Connection from the connection menu). They'll also need to enter the password you set up earlier (which we made "easy2guess" above). And now they can see your site.

<h4>Tweak Settings</h4>

If it's slow, the Viewer will hopefully be able to tweak the options of the VNC client they're running, e.g. reducing the resolution or the number of colours.

<h4>Shut it Down</h4>

When your session is finished, remember to turn sharing off, which you can do via the System Prefs again or the toolbar.

<h4>Final Caveat</h4>

VNC isn't encrypted by default, so be aware that what you share with the Viewer is as vulnerable to third-party access as email and other internet traffic. The fact you use a password may give some people a false sense of security.