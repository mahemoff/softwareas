---
id: 560
title: 'Osmosoft Hackathon: WikiData, a Wiki of Companies Data'
date: 2009-07-20T19:43:19+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=557
permalink: /wikidata-hackathon-wikidata-a-wiki-of-companies-data/
dsq_thread_id:
  - "375574318"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Avox
  - Osmosoft
  - tiddlyweb
  - Web
  - Wiki
  - WikiData
---
<a href="http://www.flickr.com/photos/psd/3728223795/" title="End of The WikiData Hackday by psd, on Flickr"><img src="http://farm3.static.flickr.com/2515/3728223795_268458bbae.jpg" width="400" height="80" alt="End of The WikiData Hackday" /></a>

<h3>Osmosoft, Hackathons</h3>

At Osmosoft, we have been engaging in a one-day hackathon about every month or so. There are several benefits:
<ul>
<li>It helps us <a href="http://softwareas.com/proving-a-technology ">prove</a> our tech in a range of application contexts.</li>
<li>It helps improve and demonstrate our capabilities for reuse. Reuse can be as simple as slapping a Javascript file with inline comments on a server somewhere, or exposing a simple web service. With those capabilities in place, it's possible to build something useful in a day, just as industry hackathons/camps demonstrate.</li>
<li>It helps us spread the word about web standards and why everything needs its own URI.</li>
<li>It helps us demonstrate and gain experience in agile processes.</li>
<li>It gets us Osmosofties working together in the same place at the same time, whereas day-to-day we tend to work on products in small groups or individually.
</ul>

<h3>The WikiData Hackathon</h3>

The latest hackathon was last Thursday, July 16, which saw us collaborate with <a href="http://avox.info">Avox</a>, a company specialising in business entity data. I believe it's working in a similar space to companies like Dunn and Bradstreet and other information providers, in that they collect, verify, and report information about companies. Avox is keen to open up parts of their database and gain the benefits of community feedback - with users being able to contribute information, leave comments, add new companies, and so on. Of course, Avox is in the business of gathering verified data, so it's not just a case of making a new wiki and letting it run by itself. There remain challenges about how Avox will merge and verify community input, and how they will make it clear to users what's verified and what's not.

<object width="400" height="300"><param name="movie" value="http://www.youtube.com/v/mqWJ-ZYkeR8&hl=en&fs=1&"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/mqWJ-ZYkeR8&hl=en&fs=1&" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="400" height="300"></embed></object>

<h3>Pre-Work</h3>

We had a conversation on the mailing list about what we did last time and what could do differently for this hackathon. Like a retrospective, but over email. <a href="http://tiddlyweb.com">TiddlyWeb</a> architect Chris Dent set up some instances with sample data taken from the existing product.

<h3>Venue and Attendance</h3>

The hackathon took place in Osmosoft's office, centered around our big table in the centre of the room. Seven people from Avox, in a range of technical and non-technical roles, attended for the duration of the event. Osmosoft had five developers working on stories, a developer working on integration and mediation, and another helping with the server and offering second-line support.

<h3>Introductions and Overview (about 1 hour)</h3>

<img src="http://farm4.static.flickr.com/3451/3739163764_8400b346fc.jpg" style="width:400px;"/>

We went round the table and everyone introduced themselves. Jeremy Ruston explained "what's in it" for Osmosoft, as outlined above, and Ken Price outlined Avox's interest in building wikidata. We also looked at the <a href="http://wiki-data.com">existing product</a>. We then had a discussion which was mostly Osmosoft people asking Avox people questions about the nature of their business, the technologies involves, and their vision for wikidata. <a href="http://whatfettle.com">Paul</a> began writing down stories on flashcards during this time.

<img src="http://farm3.static.flickr.com/2504/3739161380_32a1ab16d8.jpg" style="width:400px;"/>

<h3>User Stories (about 1 hour)</h3>

We finished writing stories - this was somewhat in parallel to the previous activity - and put them all up on the wall, with the magic of Blu-Tac. The stories were in the form "As a (role), I want to (task), so that I can (benefit)". With about 20 stories, it was useful to organise them, so we grouped them according to the role. The main roles were for Avox staff and general users. There were also some stories involving 3rd party developers and employees of companies listed in the wiki.

Everyone gathered around the stories, we read them out, and we all agreed on priorities. We didn't worry too much about ordering the stories at the bottom as it was unlikely we'd get to them during the event; if we did, we could prioritise later.

<img style="width: 400px;" src="http://farm3.static.flickr.com/2672/3739165554_f91a1374ec.jpg">

What we ended up with was a solid idea of the steel thread we were building. It would mostly be standard wiki functionality, but applied to the particular data and context of companies info. We had some bonus stories we could implement if we had time, like comments and tagging.

<a href="http://www.flickr.com/photos/psd/3731275681/"><img src="http://farm3.static.flickr.com/2527/3731275681_2346c669fe.jpg" style="width: 400px;"></a>

<h3>Planning and Infrastructure(about 30 minutes)</h3>

Developers put their initials against the first story they'd be working on, and likewise each story needed a customer representative to initial the story, so they would help refine requirements. In the event, we didn't talk all that much with customers during development; it's obviously an extremely important thing to do in a real project, but when you're wanting to get real functionality out in a day, the cost of a conversation is relatively high and the benefit to the task is relatively low. It would have been different in a 2-3 day event, or with certain stories that are highly specific to the domain. The main thing was to checkpoint with customers to check that we're generally on track.

Around noon, we drew up a timeline and agreed on a hard stop at 7pm. This means we timebox - the time is fixed and the only variable is the number of stories that get implemented in that time. We then got into 

<img src="http://farm3.static.flickr.com/2607/3739165214_1342ab45c7.jpg" style="width:400px;"/>

<h3>Development Sprints and Standup Meetings (about 6.5 hours)</h3>

We developed in sprints, with standup meetings in between. It was felt the previous hackathon's hourly sprints were too frequent, so in this case the plan was every 1.5-2 hours; we decided at the end of each standup when the next would be.

Most of us developed against the user stories. We also had a very useful role fulfilled by <a href="http://fnd.lewcid.org/blog/">Fred</a>, who was designated as a general "helper" and mediator. This was the result of our feeling that things were sometimes disjointed in previous hackathons - not enough focus on integration and infrastructure. I feel that this role was very useful and Fred fulfilled it admirably, although at times he probably felt like he had 400 people talking to him at once! We also had Chris Dent working remotely to ensure the TiddlyWeb server was running and help deploy to the live site.

The tool we developed was a standard Javascript/JQuery web app (ie nothing to do with TiddlyWiki) talking to the TiddlyWeb server.

At the start, we intended to write the web app and talk to the live server. But it soon became apparent that we would step on each others' toes by doing this, and opted for a more conventional setup where we each have our own server instance. We also had a quick debate about version control - github, private osmosoft repository, or tiddlywiki repository. This is a recurring debate which we ought to decide in advance next time. It partly arose after deciding to run our local copies of the server; it was felt this would be too much data for the tiddlywiki repo, so we used the private osmo svn. As for github, it would be nice to use git, but most of us are more familiar with SVN as we use the tiddlywiki SVN repo day-to-day, so it would cause too much complication to switch to git. Again, it might be a good idea for next time to use github instead, with some pre-work.

<h3>Presentation (about 45 minutes)</h3>

After the usual last-minute rush, we got a working product deployed. It must be noted that we let the "hard stop" slip by about 45 minutes, to about 7:30. Admittedly a bad practice, but it did yield some major results in this case, as it got us search, edit, and maps all working during that time.

Each of the developers explained what they'd worked on. We then gathered round the screen and walked through the app. Avox gave their thoughts, I recorded the video above while others broke out into informal conversations, and by that point, it was pub o'clock.

We were able to produce the steel thread we'd been planning; the key stories were demonstrated. We also implemented commenting and Google Maps integration. Being based on TiddlyWeb means we had also produced a working API "for free"; it's just the nature of TiddlyWeb as a RESTful data container. (On a personal note, commenting was the main thing I did - I extracted the comments feature from <a href="http://scrumptious.tv">Scrumptious</a> into a standalone plugin, and integrated it into the emerging WikiData product. I'll post about that separately.)

<a href="http://www.flickr.com/photos/37184970@N00/3739169608/" title="Wikidatathon by mahemoff, on Flickr"><img src="http://farm3.static.flickr.com/2581/3739169608_e4a73789f5.jpg" width="375" height="500" alt="Wikidatathon" /></a>

<a href="http://www.flickr.com/photos/37184970@N00/3739167786/" title="Wikidatathon by mahemoff, on Flickr"><img src="http://farm3.static.flickr.com/2604/3739167786_5c94f662fb.jpg" width="375" height="500" alt="Wikidatathon" /></a>

<h3>About the Video</h3>

I recorded the video above at the end of the event. One of my bugbears about hackathon events is that people spend all day coding and setting up infrastructure, and it inevitably comes down after that, or gradually falls apart as various third-party services close, databases get corrupted, people forget to keep hosting it, etc etc. In other words, you have to assume the online result of any hackathon event is transient. This is unfortunate, because the deliverable should be something that people can use to decide what happens next, whether to fund a project, and so on. While meeting minutes are often a waste of time, the artifacts that emerge in a workshop are critical to followup.

For that reason, I am perfectly passionate about taking a screencast or video to capture what took place in such events. Thanks to Paul and Ken for taking part in it.

<strong>Update:</strong> Avox CEO Ken Price (who appears in the video), has published a <a href="http://avoxinfo.blogspot.com/2009/07/wiki-data-development-with-btosmosoft.html">summary of the event</a>.