---
id: 1873
title: 'Chrome Apps v2: Native-Grade HTML5 on a Desktop Near You'
date: 2012-11-20T18:17:05+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1873
permalink: /chrome-apps-v2-native-grade-html5/
categories:
  - SoftwareDev
---
I went yesterday to Google's [Chrome Apps hack day](https://plus.google.com/116059998563577101552/posts/Pfw2xEt49XC) at Google Campus. A lot of what you hear about the new Chrome Apps is actually a v2 of the packaged app concept introduced in 2010, but focused on making apps more native like. I've followed this closely, but didn't get hands-on until yesterday.

I'll outline my initial thoughts here. For context, I hacked on a long-planned app to sync podcasts offline according to account settings ([show me the source](http://github.com/mahemoff/player-chrome)), and got as far as a scrapp that shows and plays latest episodes in all of the user's starred channels.

![](http://i.imgur.com/18KM7.png)

As I'd booked Campus's swish studio for a couple [HNpod recordings](http://www.hnpod.com/episodes/bring-back-the-40-hour-work-week-personal-outsourcing-how-to-name-your-startup), I didn't get time for the offline components, but did discuss options with Chrome team.

### Desktop For Now

We should firstly say that this is a desktop play. Of course, the elephant in the room is Chrome for Android, a fine marriage of two products from the same organisation that is releasing this, and it's running on mobiles, tablets, and TVs. So the eternal dream of HTML5 Everywhere might one day be carried forward by this initiative. But for now, this is all about the desktop. And that's a fine place to start...I'd think of it as Browser++ instead of Mobile Apps--.

### Native-Like User Interface: Seriously Competitive

This is a major improvement over the original apps model and certainly in the direction I'd hoped for in the v1 era of Chrome apps. This is much more like the Adobe Air vision of write-once, run-many, native apps that sit in their own window. You don't see browser Chrome and apps don't even need to use a standard title bar...you can roll your own there too (Yes, you too can design a lickable 1990s MP3 player with custom title bar!). Adobe Air's vision was actually very promising and certainly did well in the form of TweetDeck, Destroy Flickr, and others. But Adobe let the runtime languish, particularly the HTML5 runtime. And the Flash runtime dwindled along with Flash itself. In contrast, this is Chrome's leading-edge HTML5 runtime. Gloves are off, native apps!

The caveat is that presently, it's launched through Chrome and apps don't launch from start menus, task bars, etc. The team has aspirations to fix all that and make the apps feel truly native, much like Adobe Air apps, but it's obviously a lot of work, has standardisation implications, and remains to be seen if they will make good on that aspiration.

### Native APIs

It's not just a native UI. It's native APIs. I mean, you can write a freaking IRC server in the browser! Someone has. Check out [the servers](https://github.com/GoogleChrome/chrome-app-samples) in the app samples.

This is great and one of the main things missing from web apps right now. That said, it does lead to another challenge which Chrome team and devrel needs to solve: Too Much Choice!

![](http://i.imgur.com/uV3qX.jpg)

In my case, I had to ask the question: Where am I syncing these podcast files to? Google Drive space? FileSystem API space? Or raw filesystem, given that Chrome apps can actually save files on the regular hard drive! FWIW my answer, in my specific case, FileSystem API, because it's perhaps the most likely to be auto-sync'd in the future and doesn't have the extra barrier of Google Drive. But the decision tree is far from clear. Just as HTML5 gave us purpose-built APIs for the hacks of Ajax era, Chrome apps are ushering in a new era where there will be a third way to do everything: Pure native. And it's not always clear which way is the right way.

### Distribution Model: Potentially Confusing, Potentially Solveable

Distribution is presently planned to happen through the Web Store, but may also change in the future. I think this may be a point of confusion for users, given there's really no obvious tie to Chrome. Why install a standalone app from inside your browser? I presume the App Store itself might gain a more native look-and-feel and hopefully the Chrome team can provide a path that is intuitive for users, while maintaining the security benefits this approach affords.

### Build Process

You don't need a build process. You can just manually hack the manifest and build a single page app. But this is from the team that made Yeoman, and Yeoman's [Addy Osmani](addyosmani.com) was on hand, so I tried it out. Once installed, Yeoman supports a <tt>yeoman init chromeapp</tt> command to auto-build a Chrome app project, so this will make the process simple. I did encounter a couple of basic bugs, which Addy's aware of and will fix soon. Moreover, the fundamental issue right now is combining Yeoman targets. Right now, you can only initialise with a chromeapp or an Angular app or whatever...but not all of them. Addy well understands this problem and the next version of Yeoman will allow you to initialise with several targets simultaneously. So you could initialise a Chrome App that is powered by all of Angular, Bootstrap, and Testacular, for example.

### Debug Process: Most Improved

Chrome app development is much easier than it was a couple years ago, thanks to some small but powerful additions. Instead of hacking URLs to find the background page location, there's now a direct link. Instead of disabling and enabling the extension, there's now a reload button. And so on. It's still in need of more basic UX - put a developer in the UX lab and watch them debugging for an hour - but much better than it used to be.

### Content Security Policy

This isn't specifically about Chrome Apps, but is closely related from an end-developer's perspective. With the new CSP setup, apps are much more restricted in terms of dynamic constructs like <tt>eval</tt> usage. The net effect is that a number of libraries don't work in Chrome apps, e.g. libraries like jQuery Templating and Underscore templating. I found lodash's default build doesn't work either. My main feedback here to Chrome team would be to work with those API developers to make CSP-friendly implementations, and to guide developers 
on which libraries are working right now.

### Window-Background Page Interaction Model: Still Confusing

The background page is the same background page concept used in Chrome extensions. It's an invisible HTML page for your app that's always present when the browser is on. It's the thing that does basic polling and crunching behind the scenes.

As with Chrome apps of yore, there is still a fundamental Something's Not Quite Right tension with background pages. It's a rather complex interaction model for just basic communication between the background page and the UI windows, and never a true sense of which component, if any, is in charge. Again, it feels like some good old fashioned UX style research would solve this. What are devs trying to do? There really needs to be a better library/API and documented patterns to guide developers on the basic communication model between background windows and the rest of the app. (Not just UI windows, but also things like context menus and content scripts, when we're talking about extensions.) I cobbled together a little Pub-Sub type approach which feels like the right way to do it, but it shouldn't be anything an app developer needs to even think about.

### Standardisation or No?

I've said this before, but fragmentation is a huge threat to the web right now, because the miserable alternative seems to be trailing years behind native apps while debating on standards. In six months, we will have a perfect litmus test, because Firefox OS will by then be in production and using similar native-like APIs to Chrome. The question is, will they be the same APIs or not? I haven't seen a lot of evidence these really deep-impact APIs, like background processing and notifications, are being standardised, but I'm only a casual observer. What I can say is that if they're not being standardised effectively, then efforts like Chrome apps and Firefox OS won't make much of a dent in the onslaught of native platforms. Best I could hope for in that case, as a pragmatic developer who is ultimately motivated by the needs of end-users, is a tighter integration between Chrome and Android.

### Conclusion

So, yesterday's workshop left open a lot of questions about project direction, but also a lot of hope for the HTML5 and Chrome platforms. All that depends on how well developer feedback is taken on board, and devrel is certainly doing its part to make that happen on the basis of what we saw yesterday.