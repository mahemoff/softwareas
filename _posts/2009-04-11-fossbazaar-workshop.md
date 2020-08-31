---
id: 530
title: FOSSBazaar Workshop
date: 2009-04-11T03:00:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=527
permalink: /fossbazaar-workshop/
dsq_thread_id:
  - "375574173"
categories:
  - SoftwareDev
tags:
  - Conference
  - FOSS
  - FOSSBazaar
  - Osmosoft
  - TiddlyGuv
  - Workshop
---
<a href="http://fossbazaar.org"><img src="http://img140.imageshack.us/img140/8610/picture1257.png"></a>

I've been at the FOSSBazaar workshop in SF for the past couple of days - an afternoon session and a session this morning. It's part of the Linux Summit, FOSSBazaar being a workgroup of the Linux Foundation (though it's not Linux-specific). (It was news to me that Good Friday isn't an official public holiday in the US.) <a href="https://fossbazaar.org/">FOSSBazaar</a> is an industry consortium focusing on open source usage in the enterprise, in particular open source governance. I  attended because I have been developing a tool at Osmosoft to support enterprise open source governance, codenamed TiddlyGuv. I'll say more about TiddlyGuv in the next post, but here are some notes I recorded at the session.

The notes here are mainly from yesterday's session - brainstorming about where FOSSBazaar should be heading and what activities to perform. Today's session was several presentations, one being mine on TiddlyGuv. For the record, the talks were: Krugle, Osmosoft overview (from my colleaugue Andrew Back), TiddlyGuv (me), INRIA, Qualypso, and Fossology (another open source project in this space which we've talked to previously and will hopefully collaborate with in the future; more in a later post).

These are iphone notes; spelling and grammar caution!

FossBazaar - Open source governance community - managing open source within an organisation - Share best practices ...

started in jan 2008.

State of FOSSBazaar website: Blogs are healthy, forums need attention - would be good to have some discussion amongst ourselves. Whitepapers could be added to.

Qualypso project overview: an organisation encouraging open source adoption esp in Europe. Aiming to set up 6 competence centres -initially some funded by European commission and eventually private or regional funded.

mention of EUPL - recent European license - some unusual features - translated into multiple languages and gpl-compatible

Discussion about what kind of people are targeted by FOSSBazaar - important to think about developers not just managers/lawyers/etc because (a) they can often be an entry point into other parts of the organisation; (b) they often have policies forced on them so regardless of their view, good to target them too to support and promote open source usage. eg should I be using GPL?

Discussion about projects fossbazaar partner could collaborate on to add value and raise profile. The value compared to other organizations would be to offer expertise and experiences from the real world of organisations/companies. Most of the session involved brainstorming those projects. There was a pragmatic focus on packaging the info up neatly as handbooks, "top 10" lists etc, and thinking about SEO. The notes from this brainstorming session were written up during the meeting and I can reproduce them below (thanks to Ragavan Srinivasan who wrote them up during the meeting and Martin Michlmayr for making them available).

<hr>
Potential ideas:

* Common patch contributor agreement â€“ SFLC may be working on this.
SFLC and LF are working on this
* Authoritative source of license information: scan code; there are legal issues
* Standardized way to communicate license to users (README? INSTALL.TXT?LICENSE.TXT? XML?) Document/Guidelines?
 * SFLC published a legal primer that could serve as a starting point. (Need link)
 * Maybe a â€œHOWTOâ€ or cookbook could be added to primer
 * Get projects on board who will adopt the process
 * Potential projects to work with as pilot: Apache, Eclipse (may already be doing this?), KDE
 * Should this expand beyond just license text standardization to IPR policy standardization along the lines of what Eclipse seems to be doing? 
 * Publish Wall of Fame with a badge.
* Open source governance best practices guide book
 * Benefit if done by a neutral organization
 * Create editorial structure, then get content from each of the partners
 * e.g. creating an OSRB, what to include in a policy
 * FOSS Governance Fundamentals document is quite updated; this one could be more detail
 * Ask Andrew/Olliance for content
 * Create outline, then ask partners to contribute
* General guide on the licenses, how to interpret them
 * Three books (Rosen, St. Laurent, Van Lindberg) â€“ perhaps we should link to them on FB?
 * Icons to represent licenses ?
* Survey data?
 * Governance focused (do we have an analyst company as a partner?)
 * Ask TonyW if a student who could do this
 * Start by making a survey of LF members; but that won't include end-users
 * Make it repeatable; do it every quarter or year
 * Look at trends
 * Ask multiple people in one company and compare what they say (production, developer, manager etc view); show gaps in knowledge
* Top 10 list of considerations (vulnerabilities, distributing software that contains GPL, license/legal papers; etc.); make sure solutions are included, not just problems or risks
* Interviews with companies that have mature FOSS governance processes â€“ HP, others? QualiPSo member
* Common problems with popular FOSS libraries (tomcat, gSOAP etc.)?
 * Work with the projects to get answers (Ask FB)? 
 * e.g. Project may have no clear license, work with the developer and remove ambiguity.
 * Magnifying the fine print on some projects/licenses.
* World's funniest license interpretations by developers/businesses (funny in a scary way)
* What to do when you are undergoing some major business changes? (Mergers/acquisitions, divesting part of your company, etc.)
* FOSS licensing for Dummies?
* Read this before you do anything else list?
 * SFLC primer?
 * Books from above?
* FTF (Freedom Task Force) has a lot of documents that are in draft stage, but perhaps we could host them on FB?
* Grab fossbazaar on identica/twitter before someone squats!
* Content syndication â€“ cio.com, etc.
* Outreach to India, China, Eastern Europe, etc.?
* L10N of content?
 * How do we get the community to help with this?
 * Hugely important.
* Hosted version of FOSSology? Legal issue? Competing technology? 
 * Concern: You may end up with a comment board, all prefixed with IANAL. Problems, but no fixes
 * Why could we not adopt a Coverity/security remediation style approach? 
 * Would BD/Palamida/Others be interested in doing this as part of FB (give open source projects access to their Tools behind closed doors as a way for the projects to earn the badge) â€“ will need to address confidentiality, record keeping. We also need more lawyers to donate time to SFLC.
* A policy builder that OpenLogic has built?
* Some kind of tooling on FB (like an iPhone app people want to share, just as an example)
* Start with a small set of core FOSS projects, see if we can get them to standardize on how they represent licenses, give them badges and use them as examples to go after more FOSS projects. This allows us to fix the license ambiguity problem at the root instead of every downstream user having to resolve this.
* Perhaps we can have projects publish testimonials, maybe start with new projects or projects that don't have a lot of adoption yet. 
* What are some non-license/legal issues we want to work on?
 * Have a better reputation and build more credibility.
* Case studies gets another vote. Be generic so you don't have to name names. 
* Boeing, Lockheed, BAE, BT, all have talked about their open source governance best practices in public. AFIS conference (DoD conf. On FOSS). We have presentations.
* Forums: what are the strangest place you've found licenses in?
* Forums: OSRB: to allow companies to have comparisons of OSRB

User categories:

* My company won't let me use FOSS â€“ HELP!!!
* My manager thinks we don't use FOSS â€“ how do I break the news?
* What is this FOSS thing I keep hearing about?
* I've been asked to create an OSRB/FOSS Center of Excellence for my company â€“ what do I do?

Marketing
* Top 10 theme related to governance
* SEO
* Social networking
* Reach out to journalists
* Webinar series (lead generation)
* Press releases
* Get more in-bound links: e.g. syndicating content
* Create more partnerships & get links: e.g. with QualiPSo
* Newsletter
* Twitter: e.g. most active forum topic this week

Next steps:

* Add â€œbest practicesâ€ on FOSSBazaar
* Create outline for Governance best practices document
* Define use scenarios (e.g. â€œnew to open sourceâ€) and show content depending on what they need
* Top 10 lists
* Interviews
</i>