---
id: 440
title: 'Testing OpenSocial Apps &#8211; Current Challenges'
date: 2008-04-16T08:19:57+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=437
permalink: /testing-opensocial-apps-current-challenges/
dsq_thread_id:
  - "375409658"
categories:
  - SoftwareDev
tags:
  - Ajax
  - Facebook
  - Gadgets
  - OpenSocial
  - Widgets
---
<img src="http://picupper.com/2008/04/16/opensocial.jpg"/>

At present, the OpenSocial containers are new and the whole process is still quite difficult from a developer's perspective. These are unfortunate barriers to adoption which the containers could overcome with some redesign.

The challenges at present are:
<ul>
  <li><b>Manual signup and approval process required.</b> Even to get onto the sandbox area, you have to go through a manual signup and approval process, which usually takes a day or two. A human is in the loop verifying your details. At that time, the developer may have lost interest, or the mail may never get to them.</li>
  <li><b>Lack of test accounts.</b> The sandbox accounts usually can't interact with non-sandbox accounts - that's what makes them "sandboxes" and this is a wise policy. However, what do you do, as a developer, when you want to test with a large group of friends? You could friend other developers, but testing is going to get a little tired if you have to keep asking them what happened. The problem is the manual signup process - you have to add new users with fake details for approval by the container - weird! On Orkut at least, you can also invite friends from your test account, so it's possible. And, oh yeah, I hope you get a kick out of CAPTCHA. You'll be filling in a *lot* of CAPTCHA forms as you build up your social network of imaginary friends! One to create the account, one to verify email, one for good luck here, one more just because why not. And that's for each user on each container! If I was running these containers, I would make it even simpler and just create an initial block of 10 fake friends (some friends with each other...pick your favourite soap opera) and let the user seamlessly add new ones too.</li>
  <li><b>Older versions and Missing Features.</b> Ning and Plaxo are hosting OpenSocial 0.5, whereas 0.7 has been out for a while and 0.8 is about to come out. I can't blame them for not upgrading all the time, but it still makes development more difficult. As for missing features, I noticed this with Hi5. It's a good implementation, but still <a href="http://lindner.hi5.com/friend/group/2519935--8497111--hi5%2BSandbox--User%2BPreferences--topic-html">missing a critical feature - UserPrefs</a>. This is just the multi-container nature of OpenSocial.</li>
  <li><b>Slow code-test cycle.</b> When testing with a container, you have to change the gadget on the server and the container will then reload it and render it. This reloading process will always take some time, but the container can do as much as possible to eliminate any other delays. Unfortunately, they don't make it easy at present. I refer specifically to caching. You obviously don't want your gadget to be cached during code-test cycles. Caching is usually enabled by default, even in the sandbox. That's kind of dubious - you would think a sandbox should load the gadget each time. But okay, I can accept that decision as it's useful when you're testing the gadget 100 times not to be re-downloading it all the time. However, it's usually not clear or documented how to suppress caching when you want to. Again, the containers should be making it dead simple if they want to encourage development...how about a caching on/off checkbox somewhere in the gadget chrome or settings menu?
</ul>

There is a lot the containers can learn from Facebook, and they will need to for OpenSocial to really take off and compete against it. For comparison, here is how Facebook deals with the issues above:

<ul>
  <li><b>Manual signup and approval process required.</b> Facebook makes this completely automated. You create a normal Facebook account and simply visit a special URL to make it a developer account.
  <li><b>Lack of test accounts.</b> It's easy to create test accounts in Facebook - you just keep creating normal accounts and flipping them to become developer accounts by visiting that special URL.</li>
  <li><b>Older versions and Missing features.</b>  With Facebook, there is only one implementation, so only one definitive version of the API. There's nothing OpenSocial can do about this directly. It's simply a consequence of the "Write Once, Run Many" aspiration and the only way for the community to deal with it is to be better in other ways, and to at least be very explicit about what each container does and does not support.</li>
  <li><b>Slow code-test cycle.</b> This doesn't arise in the same way because the model is either based on an iframe directly to your site, or FBML you enter into a form. The OpenSocial gadget model - an XML sitting on a server somewhere - is neater as there's no form involved; everything's encapsulated in the XML file. However, it does introduce the whole question of caching and the containers should be doing all they can to simplify the development process to that end.</li>
</ul>

I'm a great believer in the OpenSocial vision; hence, I hope the containers will be working to minimise these obstacles. Right now, it's okay for professionals, but there are enough hurdles there to hold back an army of potential hobbyist developers from uneashing their creativity on this platform.