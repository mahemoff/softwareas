---
id: 410
title: Did you hear the one about enterprise reuse?
date: 2007-11-23T19:20:38+00:00
author: admin
layout: post
guid: http://www.softwareas.com/did-you-hear-the-one-about-enterprise-reuse
permalink: /did-you-hear-the-one-about-enterprise-reuse/
dsq_thread_id:
  - "375973999"
categories:
  - SoftwareDev
tags:
  - Agile
  - Enterprise Reuse
  - REST
  - Reuse
  - Web Services
---
Confirming that enterprise reuse can be a bit of a joke at times, Jason Gorman shares <a href="http://parlezuml.com/blog/?postid=511">this fable on enterprise reuse</a> (via <a href="http://jchyip.blogspot.com/2007/11/tale-of-tea-bags-and-reuse.html">another inspired Jason</a>). Short summary: Two ladies could save 8 cents by boiling tea in the same kettle. But the cunning analyst forgets that, since they live 20 miles from each other, there will be overheads to the tune of a $20 cab ride and the travelling time.

Viewed from a high level, enterprise reuse is a noble goal; what's the point of being a single company if everyone writes their own code? In practice, it can be fraught. Ironically, it's usually easier to reuse publicly-available libraries (e.g. open-source libs on sourceforge) and public web services than those in the same company. The following things make reuse more digestible in an enterprise setting:

<ul>
<li><strong>Language-agnostic, industry-standard, technologies</strong> Using obscure or proprietary technologies can work in an individual team, but rarely in a large enterprise; in most cases, there are simply too many factions with different skill sets and legacy code bases. There are companies that describe themselves as a "pure Java shop", for example, but you will indefinitely find pockets working in Python, .Net, and so on. Getting an enterprise to truly standardise (not just lip service) on something non-industry-standard is futile. It takes several months for people to get really competent in a new language; in an environment full of contractors and staff turning over every few years, and full of legacy systems, you can count on the fact that there will be disparate technologies at play.  It's a good thing, too; no one language (or paradigm, for that matter), not even Java *gasp*, is the right solution to all problems.</li>
<li><strong>Service-oriented</strong> SOA as in "built on a needs-driven basis". The stuff that's available for reuse is stuff that's been abstracted from real-world projects, where at least one project already built it and at least one other project actually needs it. (Rails is successful because 37Signals uses it; there aren't dozens of 24-month working groups involved.) Perhaps the biggest mistake enterprises make in this whole area is pushing out functionality no-one else actually wants to reuse.</li>
<li><strong>Support trumps standardisation</strong> The best way IMO to encourage a certain technology or library is the carrot, not the stick. Make people actually want to reuse what you have to offer, rather than forcing them to do so. I am very sceptical about any situation where architects have to act as the reuse police; if the component or service was designed, documented, easily located, and served a genuine need, wouldn't the developer be drawn towards it? Wouldn't they actually <em>want</em> to use it, and maybe even give something back to it? In an ecosystem where components and services are high-quality and easily-accessed, you can forget about mandating reuse because it will happen anyway. See <a href="http://ajaxpatterns.org/Web_API_Patterns">Web API Patterns</a> and <a href="http://softwareas.com/documentation-as-conversation">Documentation as Conversation</a> for the kinds of things that will make this happen.
<li><strong>Online</strong> As a rule of thumb, offering a centralised web service is better than offering a reusable code component. The web service can (should) be easier to use and is language-agnostic. Obviously, there are sometimes situations where code components make more sense, especially from a performance perspective. I wouldn't use an online service to create a polygon every millisecond, for example.
<li><strong>Easy to use</strong> As with any API, it should be easy to learn and make calls. For this reason, online services should be RESTful, not SOAP or CORBA or whatever MQ if you can help it.</li>
<li><strong>Iterative progress</strong> Don't try to bite off more than you can chew; if you start pretending *everything* can be reused, you'll soon find that nothing gets reused.</li>
<li><strong>Simple and parsimonious</strong> Factor out the trivial factors that relate only to one particular client. In enterprise reuse, this can be a big problem, where client projects may be the budget holder for anything reusable. It's difficult, but someone needs to stand up and say "no, we're not going to include feature X because no-one else would actually need it". In software, deciding what to leave out is usually a greater challenge than coming up with new things to put in. Any feature that won't be used by a significant proportion of client apps is going to create more clutter than its worth. In a broad-scale service, I'd say this minimum proportion should be something like 5-10% (e.g. Each method should be exercised by 5-10% of clients who used the class.) In an enterprise context, where there may only be a few clients, I'd say the criterion should be "at least 2 clients". (There was a podcast interview a while ago, with PragDave I think, where he was asked what he would include in Rails 2.0. He essentially replied that he's more worried about taking things out - push them out of the core distro and into plugins.)
<li><strong>Automated</strong> Sometimes, people think "it's all under the same roof", so getting access and learning about an API requires a call or a meeting with the owner of the reusable service/component. Whereas, if Google offers the same thing, it will provide online doco and a means of accessing it automatically, without any human intervention. An agile enterprise should aspire to do the same thing; it doesn't have to be as polished as a public offering, but the spirit should be the same. Otherwise, it won't scale, and the owner will soon become fed up doing the same thing over and over.</li>
</ul>