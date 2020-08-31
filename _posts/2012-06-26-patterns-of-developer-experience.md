---
id: 1707
title: Patterns of Developer Experience
date: 2012-06-26T16:08:42+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1707
permalink: /patterns-of-developer-experience/
categories:
  - SoftwareDev
---
[toc]

*Update 27-Jun-2012:* [Slides from my talk on these patterns](http://prez.mahemoff.com/hn-devexp) at [Hacker News London](http://lanyrd.com/2012/hnlondon-june/). 

"Developer Experience" is the practice of understanding how developers get their work done, and by extension, the practice of optimising that experience. DX is inspired by the User Experience practice and sees developers as a special case of users. We can apply principles of UX to improve our understanding of DX, and as with any applicaiton of UX principles, we also need to consider the domain itself, which in this case means programming and the software industry. Thus, DX is a combination of UX and general development principles.  

DX has many possible applications and audiences, but in the present context, we are specifically interested in ways they might inform API providers. By "API", I really mean any software or services which is used by software developers, i.e. anything where software developers are themselves the end-users. Thus, these are principles and patterns to guide the development of APIs, web services, frameworks and libraries, programming languages, and tools such as IDEs and command-line scripts. These terms are mostly used interchangeably here. For the most part, I'll simply refer to them as APIs.

Who is the audience here? The most obvious category is companies wooing developers, e.g. those who make compilers or offer APIs. However, most products eventually evolve into APIs. e.g. Flickr began life as a photo sharing website, but soon everyone was mashing Flickr photos together with Flickr's API. My own focus right now is ostensibly [a browser-based podcast app](http://player.fm) for "end-users", but certain data is actually available in various programmer-ready formats and I expect to evolve it into an engine where third-party apps could easily hook in, e.g. to get content about a particular topic, or to push new data. This phenomenon is especially the case with modern web architecture. A RESTful API is often there on day 1, lurking behind the scenes of a Single Page App. So I think developer experience is becoming an important consideration for anyone in the software industry today, even if they aren't directly serving developers.

<!-- ########################################################################## -->
<h3>Principles of Developer Experience</h3>
<!-- ########################################################################## -->

<img src='http://i.imgur.com/TrqO8.jpg' />

These design principles set up the context for our patterns. [Ade](http://blog.oshineye.com/2011/05/what-is-devexp.html) has also written up some related principles for Developer Experience.

#### Empathy Principle: Know your Developer

Designing any experience means intimately understanding those who will undergo the experience. Developers are not homogeneous, so the tool developer is not necessarily the same as the end-developer.  

For example, browser developers devote most of their energies to building browsers in C++ and operating system APIs; but their end-developers craft web apps in JavaScript and web-standard APIs. Sure, the two populations share common DNA, but let's not fool ourselves.  The web developer has different skill sets and belongs to a different community of developers with its own culture, conventions, and applications. The tool developer needs to get familiar with them.  

This principle may be less true in some cases, e.g. the "tool" is simply a library in the same programming language. Nevertheless, developers are always more familiar with their own products, so there's always a need to see the world from another's eyes. This might sound like an impossibility; how can you "un-know" something? Partly, it's simply a mindset, and a desirable one to adopt. But there are also concrete practices to make it happen, such as DOGFOODING and FEEDBACK PROCESS.  

#### Design Principle: Value Quality Design Above All Else 

Documentation is nice. Examples are nice. Support forums? Nice too. But all these support mechanisms are only band-aid solutions if the underlying system is poor.  As Don Norman has explained, you shouldn't need a user manual for a door.  Yet, many doors have Push and Pull labels because they don't make use of afforances. If someone sees a handle, they will automatically push, and if someone sees a door plate, they will automatically push.  

Think of it as a see-saw. Increase design quality, and you will need less support. Make a mess of your design, and you will need a lot of support. Moreover, your system will be less popular and your end-developers less productive. While supporting mechanism are essential too, they come a distant second to the underlying product.  

#### Trajectory Principle: Support the Road to Mastery 

Some end-user-focused systems only ever need to consider novice users, e.g. ATMs. Others can assume an enormous training effort, so they have the luxury of assuming users are fully experts, e.g. systems for aircraft control or computer-assisted manufacturing require years of learning to master. In the DX world, at least those systems which are interesting enough for us to consider, we are also aiming to support expert developers. But most tools are chosen by developers themselves, plucked off the interwebs and given a quick trial run. So we also have to support users who are novice with our own system, even if they may be expert developers. A novice doesn't become an expert overnight, so we also have to consider intermediate users. In other words, we need to support every step in the path from novice to expert.  

Some development tools are easy for novices, but don't go any further.  They might present a GUI wizard that automatically generates a new, working, project, which can be tweaked here and there. But it's not possible to get into the guts of the app. Or if it is possible, it requires a sudden leap into another programming language and SDK, thus breaking the smooth road to mastery. We are more inspired by tools which let someone get a new project up and running, and then build on it with the same concepts.  

<!-- ########################################################################## -->
<h3>Patterns of Developer Experience</h3>
<!-- ########################################################################## -->

Principles like those above say everything and nothing. They serve to establish our mindset as it applies to developer experience, but it's only in the patterns below we can see what to do about it at a practical level.  

<!-- ########################################################################## -->
<h4 class='major'>High-Level Design Patterns</h4>
<!-- ########################################################################## -->

![It just works](http://i.imgur.com/wfCGP.png)

These are cross-functional patterns which need the commitment of everyone working on the platform.

<!-- ========================================================================== -->
##### Pattern: INSTANT GRATIFICATION
<!-- ========================================================================== -->

###### Problem

There are many tools to solve a problem, and most of the time,
developers are in a rush to find one that solves their immediate problem.

###### Solution

Make the "out-of-the-box" experience work in 5 minutes or less. By analogy, think about how cool it is when you buy a new gadget and you can easily take it out of the box, switch it on (and it has already been charged, because this is a cool gadget), and play with it.  That's how cool we want to make our out-of-the-box developer experience.  

###### Examples

* With Ruby on Rails, you can create a new project by simply typing "rails project-name" and run it with "ruby script/server", which will make a cleanly-designed web app. And not a blank page either, but further info about next steps and links to online resources.

* With some tools, you can run everything in the browser. For example, CoffeeScript's homepage lets you write and evaluate a script in the browser.

* Twilio has a [fantastic out-of-the-box demo](http://www.avc.com/a_vc/2010/08/how-to-pitch-a-product.html) to build something eye-catching in just a few minutes of live coding.

<!-- ========================================================================== -->
##### Pattern: DEVELOPER PERSONAE
<!-- ========================================================================== -->

###### Problem

Every developer who uses your system will be different, and it's not effective to design for some abstract "average" user.

###### Solution

Devise a handful of "personae" to capture the main kinds of developers you wish to target. Be as concrete as possible. For example, a web framework you might identify "Joe", a front-end designer new to programming; "Sue", an experienced programmer new to web development; and "Poindexter", an all-round expert.  

<!-- ========================================================================== -->
##### Pattern: FEATURE DRIVEN DESIGN
<!-- ========================================================================== -->

###### Problem

How do you make your developers productive?

###### Solution

Consider the key tasks your developers want to achieve. This can be achieved with a combination of DEVELOPER PERSONAE and talking to real developers. Optimise your tool around these tasks. Note: In some cases, you'll need to introduce some "magic" to target these special cases and this might introduce some redundancy, complexity, or ambiguity. Such trickery goes against the grain for some people, and breaks the stereotypical programmer's mindset of keeping things orthogonal and parsimonious. While we share those goals, we think getting key tasks done is a higher priority goal. The challenge is to keep the interference to a minimum. A good example is Rails' inflection, which turns words into their plural form, including exceptions like "octopi" and "sheep". This "magic" doesn't go so far as to hard-code those exceptions, but provides a default list of exceptions which is easy configurable as code, which is a good compromise.

* The HTML5 pushState API lets developers change the current web page's title at the same time as changing the URL (<tt>pushState(state, title, url)</tt>).  This feature is technically unnecessary because there's a separate mechanism to change the title (<tt>document.title = "title"</tt>), but when two commands are often performed at the same time, it's convenient to combine them.

<!-- ========================================================================== -->
##### Pattern: LAYERED ARCHITECTURE
<!-- ========================================================================== -->

###### Problem

How do you provide powerful capabilities when the system has to be usable by novices?

###### Solution

Provide a layered architecture, where a novice uses higher-level APIs, but those APIs can be modified and configured by experts.

<!-- ========================================================================== -->
##### Pattern: DOGFOODING
<!-- ========================================================================== -->

###### Problem

How do you ensure your API is well-designed and robust before it reaches developers?

###### Solution

Eat your own dogfood. That is, use your APIs for systems your own organisation builds.

Dogfooding is a practice that can be applied to most consumer products, but takes on particular significance in the context of APIs, because many owners of APIs are also owners of related consumer products. For example, Facebook is in the perfect position to [prove](http://softwareas.com/proving-a-technology) its in-progress APIs using its many mobile and web apps. Even when that's not the case - when the organisation is a pure API vendor - it's still important to dogfood with sample apps. The devil's in the detail, and the only way to iron out problems early on is to put yourself in the place of a potential consumer of your services.

<!-- ========================================================================== -->
##### Pattern: KNOW YOUR END USER (USERS OF MY USER)
<!-- ========================================================================== -->

###### Problem

How can you deliver as much value as possible to your developers?

###### Solution

Study your developers' own users. Rare is the developer who uses your API for his or her own ends. Developers almost always develop software for others to use. In some cases, it might just be someone else in the same organisation, but that's still a different role with different needs. While it's primarily the responsibility of the developer's organisation to know their users, these details will still be relevant to your own operations, as explained in [Michael Porter's work on the Value Chain](http://en.wikipedia.org/wiki/Value_chain).

For example, you may have a cloud API for complex number-crunching. What kind of applications would integrate your solution? If it's a simulation of a nuclear reactor, and the developers' clients are government regulators, your API will need to emphasise and demonstrate precision, reliablity, robustness, and so on. If your developers are building systems for traders, they'll probably be more interested in speed and cost. Chances are, your developers' users fall in several categories, and part of your responsibility as the API owner is to know those end-users and reflect the appropriate trade-offs in your APIs.

<!-- ########################################################################## -->
<h4 class='major'>Documentation and Learning Patterns</h4>
<!-- ########################################################################## -->

![Less docs](http://i.imgur.com/vbgwy.jpg)

<!-- ========================================================================== -->
##### Pattern: CONCISE REFERENCE
<!-- ========================================================================== -->

###### Problem

How can experienced developers find details of your API without trawling through source code code and tutorials?

###### Solution

Provide concise reference documentation that gets right to the point.

* Format each API call consistently, including the same set of fields (name, description, etc.)
* Highlight what's optional and what's mandatory.
* Mention any versioning issues, i.e., if a certain feature was introduced after some version or is now deprecated. And be sure to tie the reference documentation to a particular version.
* Keep the documentation online, with consistent and clean URIs for each section, with in-page links for subsections. Linkability will help immeasurably when handling support queries. It will also help with SEO, allowing developers to quickly find the right content via search engines.
* Link to any detailed information and related tutorials.
* Consider mechanisms for community contributions, such as hosting the documentation on a wiki or a GitHub repository which people could issue pull requests too. Also, consider a comments section.

In some cases, particularly code libraries, you can embrace [literate programming](http://en.wikipedia.org/wiki/Literate_programming) and use tools such as [Doxygen](http://doxygen.org) to save time and avoid redundancy.

###### Examples

* The jQuery project has always kept easily-digested reference material online, with clean URLs such as http://api.jquery.com/category/manipulation/ and http://api.jquery.com/attr/. 
* The PHP documentation includes easily-guessable URLs such as http://php.net/strlen and also a well-moderated comments section where developers can find countless tips from fellow travellers.

<!-- ========================================================================== -->
##### Pattern: PATTERNS AND RECIPES
<!-- ========================================================================== -->

###### Problem

Developers who are unproductive will quickly seek alternatives. How can you accelerate learning?

###### Solution

Create concise "Recipes", "Howtos", or "Patterns" to explain how specific use cases are achieved. Half of the battle here is in discovering which problems are (a) frequently encountered (b) difficult to overcome. This is where the community feedback role of your DEVELOPER RELATIONS PROGRAMME kicks in.

<!-- ========================================================================== -->
##### Pattern: TUTORIALS
<!-- ========================================================================== -->

###### Problem

How can you introduce developers to broad topic areas?

###### Solution

Create high-level tutorials focused around particular features or steps on the learning curve. Tutorials should generally walk through the steps of build a complete, if limited product. The completeness of the product helps to put the API in context, and it should ideally be useful - or at least novel - enough to provide some motivation for continuing to use the API.

<!-- ========================================================================== -->
##### Pattern: ONLINE PLAYGROUND
<!-- ========================================================================== -->

###### Problem

How can you give developers a hands-on introduction without going through the tedium of downloading and setting it up?

###### Solution

Provide online playgrounds where developers can code and run apps inside the browser. For pure client-side JavaScript libraries, this is quite easy, because the playground itself will be written in JavaScript, so you can just execute what the user is typing in. It will be more work if there's permissioning involved, and you may want to support such use cases via [Cross-Origin Resource Sharing](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) or related cross-domain techniques. In many cases, though, you will need to provide some kind of emulation or console-style experience, in which the user's code is executed on a sandboxed server instance.

###### Examples

* Google has a [comprehensive code playground](http://code.google.com/apis/ajax/playground/) covering all its major APIs.
* [Many HTML5 tutorials](http://updates.html5rocks.com/2012/06/The-amazing-powers-of-CSS) include their examples as links to JSFiddle, sometimes even embedding the JSFiddle directly into the document. This way, the reader can experiment with code changes while reading the tutorial.

###### Note

Perhaps the first prominent example of the sandboxed server approach was why the lucky stiff's [Try Ruby](http://ajaxian.com/archives/try-ruby-ajax-style) project.

<!-- ########################################################################## -->
<h4 class='major'>Developer Community Patterns</h4>
<!-- ########################################################################## -->

<a href='http://articles.businessinsider.com/2011-05-11/tech/30047107_1_chrome-os-chrome-web-store-sundar-pichai'><img src='http://businessinsider.com/image/4dcac024cadcbb49701c0000/rovio-mighty-eagle-peter-vesterbacka-at-google-io.jpg'></a>

<!-- ========================================================================== -->
##### Pattern: DEVELOPER RELATIONS PROGRAMME
<!-- ========================================================================== -->

###### Problem

How can you establish a direct line of communication between developers and your company, for more technical conversations than are possible with sales and marketing staff?

###### Solution

Employ people with development experience to work within your external developer community. For a small startup, this might just be one individual; for a large company, it should be a dedicated programme. Emphasis on development experience; it's no longer good enough to put "the marketing guy" in front of a technical audience. Developers are notoriously details-oriented, cynical about mere high-level marketing messages ("it will make you more productive"), and likely to go elsewhere if they can't have their technical questions answered. For quality-of-service and credibility, it's important that  developer relations staff have a background in hands-on development work and that they have avenues to continue performing some hands-on work while engaged in the developer relations role.

Developer relations has evolved from the roles of technical evangelist, sales engineer, and support engineer, into an all-encompassing role that concerns any interactions with the external developer community. Modern developer relations entails three main functions:

* **Evangelism.** Promotion of the API to developers. This has traditionally been done with the aim of building demand at a grassroots level, but as people with technical backgrounds increasingly assume senior roles, modern evangelism may well be reaching all levels of the organisation.
* **Support.** Provision of detailed technical support.
* **Product Improvement.** Communication is a 2-way street. Developer relations involves Listening to the developer community and feeding knowledge back into the organisation. Even with modern communications, time constraints make it difficult for product developers to get a feel for the reactions of people using their work. In this sense, developer relations staff act as the eyes and ears of the organisation.

We can further divide each of these functions according to the reach of specific activities:

* **High-Touch.** One-to-one or small-group interactions with "VIP" developers and organisations. These are typically prized partners with a "hero effect" due to their size and/or prominence, (potentially) high-paying customers, and well-respected individuals who are seen as thought leaders within specific developer communities. In some cases, these high-touch relationships will arise from other business functions, e.g., sales or business development. In other cases, they will emerge from developer relations' own contacts. 
* **Long-Tail/Grassroots.** One-to-many interactions with the broader developer community. These may be conducted offline via speaking engagements, sponsorships, and simply showing up at events. And likewise, there are many online opportunities for this kind of broad-spectrum developer relations: building technical documentation, creating demo applications, participating in online discussions, social networks, support forums, and bug trackers. It's important to "go where the conversation is" rather than just hosting your own events and online forums. This means active presence on Twitter and StackOverflow, for example. As mentioned in the previous paragraph, many high-touch relationships begin via these grassroots channels.

###### Notes

[The term Technology Evangelist originated at Apple](http://en.wikipedia.org/wiki/Technology_evangelist) and continues to be used by Microsoft, Mozilla, and others. Google prefers the term [Developer Advocate](http://almaer.com/blog/developer-advocate-versus-technical-evangelist-when-names-change-the-tone), and [some companies](https://twitter.com/paddyforan/status/213656154138619904) are beginning to incorporate the "Developer Experience" terminology in their job descriptions.

<!-- ========================================================================== -->
##### Pattern: POSTER-CHILD APPLICATION
<!-- ========================================================================== -->

###### Problem

How can you show off your API's capabilities?

###### Solution

Partner with developers who can build excellent, real-world, applications with your API. This is very much within the "high touch" realm of developer relations, where you work closely with companies who are (a) popular with users or (b) willing and able to use cutting-edge APIs. (And ideally, unicorn developers who are both of the above.) Often these projects involve confidential details, e.g. a new API which will be revealed at a conference, demonstrated with several apps from trusted partners.

This is a symbiotic relationship. The benefit to you, the platform owner, is more apps running on your platform and improved credibility when developers come to evaluate your offerings. But what are the benefits to the developer using your API? The ideal answer is that your API is simply attractive enough that using it on their own product is reward enough for the developer. In practice, though, developers may need extra incentives. This is especially the case with a new API you are aiming to launch and promote, because the developer will usually want incentives to counterbalance the increased risk, instability, and lack of documentation. You can offer the following incentives:

* **Brainstorming.** Much as a good salesperson helps to "find a need", you'll need to think creatively about how your API might lead to product improvements, or maybe even a new app, pitch your concept to the developer, and co-operate on a plan of attack. As the project progresses, always be providing creative input and feedback.
* **Technical support.** Any API under development is going to be a rough ride. You'll need to help developers work through any challenges that arise. Typically it's developer relations' role to mediate between engineers on the API side and those from the partner organisation.
* **Bug reporting.** API bugs will inevitably arise and need to be reported back to the API developers, possibly using a bug tracker.
* **Promotion.** Promote partner apps at events, press releases, and blog posts surrounding your launch. This is a win-win situation. In  addition, consider an ONLINE SHOWCASE to promote a wide range of partner apps, as well as featuring apps in catalogues or store targeted at end-users.
* **Resources.** In some cases, API providers will provide actual developers (including designers, etc.) or funds to pay for developers. Factors making this scenario more likely are: (a) the partner is a well-established brand; (b) the API is new and unproven (given that more established partners tend to be more risk-averse); (c) the API would require significant learning curve for this particular partner; (d) the API is a user-centered platform (i.e., we are encouraging the partner to build an app users are demanding).

In some cases, platform companies will not only provide technical support, but more tangible support in the form of funds or developers.

###### Example

The New York Times app was prominently demonstrated when Apple introduced the iPad. Given the immense secrecy around this launch, one can safely assume a large amount of co-operation between the two companies in prior months. You'll see evidence of similar partnerships at Google IO and other events where products are launched.

<!-- ========================================================================== -->
##### Pattern: ONLINE SHOWCASE
<!-- ========================================================================== -->

###### Problem

How can you promote apps using your API?

###### Solution

Gather apps together in an annotated online showcase/gallery. The purpose is to highlight POSTER-CHILD APPLICATIONS, including those not prominent enough to be headline acts in conferences. The showcase provides credibility to your API, serving as [social proof](http://en.wikipedia.org/wiki/Social_proof). It can also be food for thought for designers considering how to use your API. And lastly, it can serve to promote the app, at least among the developers and journalists who may be browsing the showcase.

Don't assume users will take the time to install any apps or even visit relevant websites. Instead, provide a separate page for each app where you overview the app and include relevant screenshots and videos. Moreover, include technical details targeted at developers, e.g. which specific API calls were made and what challenges did the developers have. You may wish to include intervies with the developers.

This pattern is closely related to an app store. If you have an app store, plugin repository, or similar, your curation of featured apps serves some of the same purposes as a showcase. However, the audience is different, so you will still probably want a separate showcase targeted at developers.

<!-- ========================================================================== -->
##### Pattern: TEST DEVICES
<!-- ========================================================================== -->

###### Problem

How can developers try out your API if it runs on expensive devices?

###### Solution

Give out, or loan, devices to developers. Many hardware companies will give out freebies to journalists and business leaders, but it's equally important to get those devices in the hands of the people who will build the applications. While developers can sometimes work with emulators, there's no substitute for debugging and testing on the real device.

<!-- ########################################################################## -->
<h4 class='major'>Implementation Patterns</h4>
<!-- ########################################################################## -->

<img src='http://i.imgur.com/HwhhV.jpg' width='250' />

<!-- ========================================================================== -->
##### Pattern: IDIOMATIC API
<!-- ========================================================================== -->

###### Problem

How can you reduce friction for developers learning your API?

###### Solution

Follow the conventions of the languages and frameworks your API is designed in. If you have a web service, this means following the conventions of HTTP and REST. If you have libraries in various languages, avoid the temptation to auto-generate them all from a common base. Instead, have their interfaces designed and battle-tested by people familiar with the language. Make them fit culturally.

###### Example

[Cloudinary](http://cloudinary.com/faq) is an example of a web service with "wrapper libraries" (Facades) for Ruby, PHP, Python, and other languages. Each library presents the same basic functionality, but in the style expected by users of those languages.

<!-- ========================================================================== -->
##### Pattern: TOOL PLUGINS
<!-- ========================================================================== -->

###### Problem

How can you reduce friction for developers using your API?

###### Solution

Build or fund plugins for popular developer tools, which helps developers work with your API.

<!-- ========================================================================== -->
##### Pattern: BACKWARD-COMPATIBLE API
<!-- ========================================================================== -->

###### Problem

How can you evolve your library without breaking existing clients?

###### Solution

Ensure newer versions of your API don't break older clients. This sounds simple, but is not something platforms always follow in practice.

Of course, the major downside of this approach is that it can restrict freedom to evolve. It will also make the whole project more tedious, being increasingly focused on testing rather than product improvements, which in turn will lead to lack of morale among staff. Look at VERSIONED API as a complementary pattern.

###### Reference

Joel Spolsky wrote a well-cited article about the success of [Microsoft's 1990s-era obsession with backward compatibility](http://www.joelonsoftware.com/articles/APIWar.html).

<!-- ========================================================================== -->
##### Pattern: VERSIONED API
<!-- ========================================================================== -->

###### Problem

How can you evolve your library without breaking existing clients?

###### Solution

Clearly delineate compatibility-breaking upgrades and continue to support previous versions for some time. A common convention is to only ever break compatibility on major versions. So version 2.2 should not break compatibility with version 2.1, but version 3.0 can. And in this case, you should continue supporting 2.0 for some time, while using your DEVELOPER RELATIONS PROGRAMME to encourage and support upgrading to the new version.

Exactly how long to support the old version is a complex question that is as much about the business you're in as any technical factors. One guideline is to support the current version, and two previous major versions. But again, it all depends.

###### Example

Google Maps has been running on [Version 3](https://developers.google.com/maps/documentation/javascript/) since May 19, 2010 - 2 years since time of writing - but Google continues to support [the Version 2 API ](https://developers.google.com/maps/documentation/javascript/v2/) and host related docs.

<!-- ========================================================================== -->
##### Pattern: MEANINGFUL ERROR MESSAGES
<!-- ========================================================================== -->

###### Problem

How can you help developers move past errors and confusing situations?

###### Solution

Provide meaningful alerts and error messages. This will help developers be productive with your API and reduce their frustration with it.

Guidelines for error messages are well-understood in user experience literature and these guidelines translate well to error messages in a developer experience context. Jakob Neilsen has [summarised error message guidelines as](http://www.useit.com/alertbox/20010624.html) as: explicit, human-readable, polite, precise, constructive. The last point is perhaps the biggest thing missing from many software error messages. At the least, you should provide links to documentation which will help to resolve the error. You can even go further in some cases by suggesting possible causes and remedies.

In the case of web services, follow the conventions of HTTP and REST in using the correct status codes for errors, as well as providing hyperlinked messages in the headers or body, as appopriate.

###### Example

Ruby on Rails has several examples of proactive error messages. An impressive example is how it will [provide a list of synonyms](http://softwareas.com/how-rails-handles-use-of-reserved-keywords-wow) when you try to use a reserved word. This might be seen as gimmicky by some, but really conveys a wonderful sense of software that is ["on my side"](http://c2.com/cgi/wiki?OnMySide). More famously, [Rails has the whiny nil setting](http://blog.bigbinary.com/2008/06/23/why-the-id-of-nil-is-4-in-ruby.html) to make it obvious when a null object is incorrectly refenced. 

<!-- ========================================================================== -->
##### Pattern: CUSTOM DISTRO
<!-- ========================================================================== -->

###### Problem

How can you help developers trade-off size and functionality?

###### Solution

Provide customised distributions of library code, where developers can easily pick the components they need.

Although storage costs for libraries is negligible these days, size still matters when it comes to performance. A larger footprint means more processing time and also longer download times in the case of software which is downloaded or deployed over the web. Furthermore, security-concerned users want to deploy software that is as minimal as possible, in order to reduce the overall risk surface and the related review effort.

###### Example

[Modernizr](http://modernizr.com/download/) provides a "kitchen sink" developer edition with all functionality intact and full source code. For production, it allows developers to configure a specific version by selecting checkboxes representing various features. As is common with many JavaScript libraries, it also provides an option to compress the package.

<!-- ########################################################################## -->
<h3>Appendix: Related Patterns</h3>
<!-- ########################################################################## -->

###### Events

* Hacker Space http://hackerspaces.org/wiki/Design_Patterns
* Hackathon
* Conference
* Forum

###### API Design Principles

* Robustness Principle
* Open-Closed Prinicple: Microkernel+Plugins
* Modularity Principle
* Convention Over Configuration Principle
* Coherent Principle
* Don't Repeat Yourself (DRY)

<!-- ########################################################################## -->
<h3>Appendix: Related Reading</h3>
<!-- ########################################################################## -->

A few of us ([Ade](http://oshineye.com), [Pamela](http://www.pamelafox.org/), [Paul](http://paul.kinlan.me)) have been accumulating resources on Developer Experience at http://developerexperience.org and more recently on a [Google Plus Developer Experience page](https://plus.google.com/116834904360889286443/posts). Also tweeting on #devexp hashtag and sometimes from @devexpftw.