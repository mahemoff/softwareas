---
id: 416
title: Taking Browser Tabs Seriously
date: 2008-01-31T00:33:59+00:00
author: admin
layout: post
guid: http://www.softwareas.com/taking-browser-tabs-seriously
permalink: /taking-browser-tabs-seriously/
dsq_thread_id:
  - "375160598"
categories:
  - General
  - HumansAndTech
  - Links
  - SoftwareDev
tags:
  - AjaxPatterns
  - Favicon
  - Javascript
  - Links
  - Web
  - Web 2.0
---
<img src="http://img254.imageshack.us/img254/5568/browsertabsvv3.png" style="width:300px;" />

I've just updated my favicon library, which I first <a href="http://softwareas.com/dynamic-favicons">wrote about here</a>. I'll explain more about the update in a separate post. For now, I want to talk about browser tabs.

Browser tabs were introduced by Opera. Then Firefox adopted them a few years later, as did Safari. Then Microsoft stepped into the '90s with their own IE tabs. Meanwhile, tabs became teh coolness and Kevin and Alex joked on Diggnation about how you could get brownie points by saying it's a tabbed interface. And so you get <a href="http://softwareas.com/tabbing-terminals-and-apples-popup-bug">tabbed terminals</a> among other things, and fortunately there is some consistency on keyboard shortcuts (typically ctrl-t to make a new tab and ctrl-w to close it, or option-t/w on mac).

We've outgrown the rudimentary functionality that is available for managing tabs.

<strong>The browser is the new operating system, the tab is the new system process, the tab bar is the new taskbar.</strong>

Power users struggle to keep up with 20+ browser tabs and grasp what's inside them. The <a href="http://addons.mozilla.org/firefox/addon/1122 ">Firefox Tab Mix extension is a superb addition</a> and should be part of the core. But there is a lot more that could be done, for instance:
<ul>
  <li><strong>Notifications.</strong> The whole issue of attention and notifications needs re-thinking in light of the new world of rich web apps. Quintessential example is web chat - how do you inform the user someone has sent a message, in another window? The favicon library helps here, and the update in my next post, helps a bit more. Playing a sound is also possible. Still, I would like to see API support for ambient dialogs, like Growl/Snarl and the Windows "sunrise" notfier that emerges from the taskbar (what's it called officially?). And sound. It's 2008, why can't browsers issue a single beep like a good 1970s PC, without requiring flash or <a href="http://ajaxian.com/archives/sound-with-javascript-but-not-flash ">unreliable</a> <a href="http://www.ajaxonomy.com/2008/ajax/cross-browser-sound-flash-only-as-a-last-resort">hacks</a>!!! Speaking of sound ...</li>
  <li><strong>Where's that sound coming from?</strong> <a href="http://softwareas.com/wheres-that-sound-coming-from">There's a sound in my browser, but I don't know where!</a> Tabs should provide a visual indication if a sound is emerging from them.</li>
  <li><strong>Default/Custom Favicons.</strong> If a site doesn't have a favicon, browsers show nothing. Bzzzt!!! They should provide more sensible defaults, e.g. at least show the site's background colour or a thumbnail of the first image. Something to make them all different from each other.</li>
  <li><strong>Provide a Summary List.</strong> Like clicking on Ctrl-Alt-Delete in Windows to get a task list or "ps" in Unix. You'd be able to see how long each tab has been open, memory usage, other excitement.</li>
  <li><strong>Hover info</strong> Similar to the previous point, let web developers provide tooltip info which will be displayed as the user hovers over the tab.</li>
  <li><strong>Popup menus</strong> Why even open up a web page? Sometimes, you want to do something quickly without having to switch tabs. Let web developers create site-specific popup menus that emerge from the tab. For example, you could use this mechanism to record simple events as they occur. Or start and stop a timer. Or to switch channels on a music website.</li>
  <li><strong>COLOUR AND STUFF!!!</strong> Browser tabs are pretty dull - just an icon and some text. Using cues such as colour and font styles, the browser could say a lot more about what's happening in the other tabs. Perhaps it could be set by the programmer or perhaps it could be set by the user (e.g. create a heatmap highlighting the least used tabs).</li>
  <li><strong>Javascript events.</strong> Javascript onEntered()/onExited() events to let the application know if it's active or not. (Similar to what desktop apps receive.) This would be absolutely brilliant for when you are notifying the user about something they need to see (e.g. a new chat message) - once they re-enter the tab, you can switch off the notification.</li>
  <li><strong>Open Forms.</strong> What about when I start writing something in a form, then switch tabs, and forget which tab has the form, or forget that it's there at all. The browser should indicate when there's a form open that you've been writing to. (Though in some cases auto-backup features may mean that's not necessary.)</li>
  <li><strong>Search.</strong> No-brainer. Browser search should work across all tabs, not just the one currently open. This would not only help you find some text, but also pinpoint one of the fifty tabs you have open.</li>
  <li><strong>Virtual Desktop.</strong> Maybe it sounds mad, but I'd like something similar to virtual desktop ("Spaces" for Mac-heads). ie Switch from "work" tabset to "social" tabset, etc.
  <li><strong>Auto-remove.</strong> Instead of forcing me to close all windows, or some random subset, or restart the browser altogether, provide some support for removing the tabs that matter least. e.g. the tabs that I haven't used for the longest and which I appear not to have interacted with (ie started editing a form), and/or the tabs that are taking up the most resources.</li>
</ul>

I'm sure there's a lot more. The main point is to take inspiration from the way operating systems let users deal with open applications, and then some. The dynamic favicon library is a small part of the solution, but there's only so much libraries and even browser add-ons can do...it needs to become a core feature of the browsers. Just as Opera and then Firefox owe a big chunk of their initial popularity to their the cult of the tab, so too do the manufacturers today have a similar opportunity to take it to the next level.