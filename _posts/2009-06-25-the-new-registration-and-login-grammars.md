---
id: 550
title: The New Registration and Login Grammars
date: 2009-06-25T17:15:05+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=547
permalink: /the-new-registration-and-login-grammars/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "376320052"
categories:
  - HumansAndTech
  - SoftwareDev
tags:
  - Login
  - OAuth
  - OpenID
  - Posterous
  - Security
  - Usability
  - Web
---
There is a well-established "grammar" for how we sign up and log into websites. Provide your name, email and password; verify the email; login to the site with username and password until you're timed out. You know the drill. But a wave of new web apps and protocols is challenging the status quo, breaking the traditional interaction patterns. In some cases, they blur the distinction between logged-in and logged-out status; and in others, they provide ways to perform privileged actions without explicitly logging in.

Before we walk through these new interaction patterns, let's be clear about the "old" pattern we've come to know and (sometimes) love. It starts with visiting a new site:
<ul>
<li> use the site anonymously. Nothing you do yet is persistent; you can look (sometimes), but you can't touch.</li>
<li> sign up by providing username, email, and password. (variants: email is *username*, password is auto-generated)</li>
<li> click on link in verification email</li>
<li> now you can log in by providing username/password and logout by clicking the logout button or by explicitly timing out</li>
</ul>

Right, you know that sequence and it works okay. However, problems remain:
- barriers to signup: perhaps the biggest problem faced by site owners is getting users to sign up. A known, authenticated, user gets a much richer experience, can contribute in mire valuable ways to the community, and can receive targeted services, not to mention targeted ads.
- barriers to login. Users might have signed up at one stage, but rarely sign in due to the hassle factor, a factor that multiplies when they have forgotten their password.
- timeout. For security reasons, timeout must happen and that <a href="http://softwareas.com/its-2007-and-most-e-commerce-sites-suck-like-its-1999">will frustrate users</a> and see them going elsewhere.
- mobile access. My dear reader may well bear the latest and greatest web-enabled digital communications circuitry in thir pocket or handbag, but the majority of phones still lack a basic web browser. Even when you do have a browser, it's difficult to login, especially if you are using suitably complicated passwords. There's something to be said for more fluid models of mobile-webapp interaction.

<h3>Lazy Registration (NetVibes)</h3>

In <a href="http://ajaxpatterns.org/Lazy_Registration">Lazy Registration</a>, an anonymous user is allowed to interact with the site right away, and through the magic of cookies or unique URLs, the site builds up a profile before the user even signs up. Once the user does sign up, they take their existing (hencetoforth anonymous) profile with them. The benefit is clear: the ability to start playing with the site without incurring the overhead of registration. The better e-commerce sites do this by letting you add to your cart as an anoynomous user; where most of those fail is they completely time you out after a short time. See Partial Logout below ...

<h3>Unverified User (Flickr pre-Yahoo!)</h3>

Here is another pattern that defies the traditionally strict dichotomy between those who are in and those who are out. You sign up as normal, but you don't have to verify the link straight away. There's effectively an "email verified" flag against your name and unverified users only have partial rights, e.g. You might be able to start maintaining content, but no-one else can see it until you're verified. The benefit here is eager users can get going right away, and have a reason to click on the verify link when they come across it later. (I'm afraid the only example I can think of is Flickr's Guest Pass concept, before they tied login to Yahoo!. I've seen it elsewhere, but can't recall where!)

<h3>Partial logout</h3>

Something like a rewind of Lazy Registration, the Partial Logout pattern allows for differing degrees of "logged-in-ness". Once a user has been idle a while, instead of completely timing them out and making them anonymous again, the system continues to "sort of" trust them by letting them view some things and keep building up some aspects of their profile. In this state on amazon, you can view your shopping cart and personalised rexommendations, and products you view will be fed into your profile; but try and purchase a book or change your credit card details, and you'll be faced with a login form. Timeout is the main reason to be partially logged out, but it might also be something else which leads the system to believe there's a risk the browser is no longer under the user's control; for example, the user logs in from somewhere else.

<h3>Device-Driven Interaction (SMS-Twitter)</h3>

You can tweet from Twitter.com or any number of web and desktop clients, but one of the main driving forces for twitter was the ability to say what pure doing wherever you are, a perfect example of SMS-driven authentication, and <a href="http://www.140characters.com/2009/01/30/how-twitter-was-born/">the reason why tweets are limited to 140 characters</a> (leaving room for a username as well).  The verification is all thanks to the caller ID. There are interesting international implications since the recipient pays in the US, while most other countries run a model where the sender pays. And when the sender is roaming abroad, they always pay to send. And it's usually an absurd amount.

A variant is MMS-Driven Interaction (e.g. <a href="http://mms.pipp.no/doku.php">Joomla MMS module</a>, although its cost - and immaturity in the US - makes it less viable. The more general way to depict this pattern is to see it as Device-Driven Interaction, where your possession of the device is used to authenticate you. Thus, a variant would be GPS-Driven Interaction, such as <a href="www.google.co.uk/latitude/">Google Latitude</a>.

<h3>Email-Driven Interaction (Posterous, Tripit, Twitpic)</h3>

Email-driven interaction is becoming really popular lately; <a href="http://posterous.com">Posterous</a> especially is taking off right now. In the simplest case, it's just emailing a new post to your blog, to a secret destination address you can see on the web page when you logged in. Where all this gets more interesting is when you don't even have an account yet! You simply send an email to their generic address (post@posterous.com; plans@tripit.com) and you're up and running. In Posterous, you can also reply to comments from the comfort of your mail client too. All this is fantastic in a mobile context, where it's often more convenient to fire off an email from your camera app than log into the website and upload it. It's also cheaper than sending MMS content around too. Of course, these services still let you log into a website the regular way too; they'll send you a link that gets you in the first time. Of particular interest is their use of simple, public, addresses. It raises the distinct risk of spoofing to act as someone else, but in practice, the services seem to be smart enough to thwart such attacks. <a href="http://www.techcrunch.com/2008/06/28/posterous-beats-tumblr-in-simplicity/#comment-2391104">Somewhat.</a> So far.

<img style="width:400px;" src="http://img.skitch.com/20090625-pr4qec878msjn4j4d162qmtaa4.jpg" />

<h3>Secret URL (SlideShare, Skitch)</h3>

A secret URL is "the login you're having when you're not having a login". (Which makes it a <a href="http://en.wikipedia.org/wiki/Claytons">"Claytons login"</a> in Aussie vernacular). A privileged user can see the secret URL, it being a long unguessable string, and can then distibute to trusted others. The chief benefit is no-one needs to log in. From the owner's point of view, they don't have to tediously list everyone who can see the resource, and it's more granular than just "only show my friends" if you already have a list of friends. Also, the owner can access it from any device or browser just by knowing the URL, and without worrying about timing out. Secret URLs are especially nice in a real-time setting (Web 3.0, here we come), where you want your friends to <a href="http://campfirenow.com">converge on a website for closed communication and collaboration</a>. The main downside of course is that it's simplistic, offering rather limited security, and in most implementations the resource must be treated as read-only, as you don't want to let people change something unless they can be held accountable for their actions. Skitch's settings for an individual image are shown below:

<img src="http://img.skitch.com/20090706-km7fhnsptthd1gsqinmg6dbqbh.jpg" />

<h3>Federated (open id-e.g. StackOverflow; Facebook Connect-e.g. CNet)</h3>

Federated login, most famously exemplified by <a href="http://openid.net/">OpenID</a>, allow for a single identity across the internet. You authorise sites with your OpenID provider, and you only need to log into your provider to access those sites. More recently, Facebook Connect provides its own brand of federated login, which is conceptually easier and simpler for users, at the cost of tying their identity to a single provider. So while purists are grizzling about lack of openness, mainstream users right now seem happy to sign in to sites with Facebook Connect, as opposed to signing up to the site separately. And sites seem keener to integrate Facebook Connect than OpenID, probably because the story is clearer for end-users, and there is a tie-in to Facebook too (e.g. site activities can show up on the user's Facebook feed). Facebook supports OpenID login, is now <a href="http://openid.net/2009/02/05/facebook-joins-openid-foundation-board/">on the OpenID board</a>, and will probably become an OpenID provider at some stage.

<img style="width:400px;" src="http://img.skitch.com/20090625-ruxbwbit3f37atmhqd13jdtagd.jpg" />

<h3>Special Mention: Delegated authority (OAuth-e.g. Twitter)</h3>

In a somewhat separate category is OAuth, the protocol that lets you delegate authority from one site to another. It is sometimes likened to giving someone a valet key, i.e. they have partial authority at your discretion and you can revoke it any time. For example, an OAuth-powered Twitter mashup will redirect you to Twitter, where you tell Twitter you accept certain actions being conducted with your account by the mashup. From that point on, until you revoke it, the mashup will be able to work with your Twitter data as if it were you. All this would be possible if the mashup asked you for your username and password, but OAuth offers a more secure model because you can moderate, track, and revoke privileges at any time. In that sense, it is unlike the other techniques here as it is less about making the service more convenient or user-friendly; and more about allowing for extra functionality by third parties, and with a hardened security model.

<img style="width:400px;" src="http://img.skitch.com/20090625-bws56gumgaq5ph7u98qn7w812g.jpg" />

<h3>Concluding Remarks</h3>

What sparked this post was the rise of <a href="http://posterous.com">Posterous</a>, which is undergoing some kind of tipping point lately. First, I heard <a href="http://itc.conversationsnetwork.org/shows/detail4145.html">the founders on Technometria</a> a few days back, outlining  their plans to provide flexible templating. Then they turn up on TechCrunch, having acquired <a href="www.techcrunch.com/.../posterous-acquires-fellow-y-combinator-alum-slinkset/">Y-Combinator stable partner Slinkset</a>. And finally, A-List blogger extraordinaire Steve Rubel <a href="http://www.micropersuasion.com/2009/06/why-i-am-forking-my-content.html">announces his new publishing strategy yesterday</a>, with Posterous playing a big part in it. All in all, a big week for a company whose key selling point is a new registration grammar.

("Grammar" is a term used by <a href="http://joshua.schachter.org/">Josh Schachter</a> at a <a href="http://strange.corante.com/2006/02/08/fowa-things-weve-learned-joshua-schachter">at a 2006 FOWA</a>.)
