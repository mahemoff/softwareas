---
id: 81
title: 'Podcast+Text: The AJAX Web Architecture'
date: 2005-04-17T23:50:45+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=81
permalink: /ajax-podcast/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
enclosure:
  - |
    http://www.softwareas.com/podcast/AJAXWebArchitecture.mp3
    28625911
    audio/mpeg
    
  - |
    http://www.softwareas.com/podcast/AJAXWebArchitecture.mp3
    28625911
    audio/mpeg
    
dsq_thread_id:
  - "375572188"
  - "375572188"
categories:
  - HumansAndTech
  - Links
  - Podcast
  - SoftwareDev
---
This podcast discusses AJAX, an architectural style for web applications that has become popular in recent months.

<a href="http://www.softwareas.com/podcast/AJAXWebArchitecture.mp3" title="This is a podcast - a blog entry pointing to an MP3" style="text-decoration: none;"><img src="/images/aquapodcastfileicon.gif" border="0" alt="Click to download the podcast mp3" border="0"/></a>

<span style="font-size: x-small;">This is a <b><a href="http://podca.st">Podcast</a></b> - a blog entry with an embedded MP3 link. On Internet Explorer, Click the left mouse button to listen, or click the right mouse buttton and "Save As..." to download. **Better yet, you can subscribe for updates straight into your PC or ipod - it's easy, open, and free.** Install the free, open-source, <a href="http://ipodder.sourceforge.net/download/index.php">Ipodder client</a> and when it starts, just paste this in: "http://www.softwareas.com/podcast/rss2". Too easy! 15 minutes and you can be subscribed to receive thousands of MP3 podcasts -  from [official BBC documentaries](http://www.google.co.uk/search?q=+site:www.bbc.co.uk+bbc+podcast) to business personalities like [Sun COO Jonathan Schwartz](http://blogs.sun.com/roller/page/jonathan/20050323#inaugural_podcast) to [scores of amateur publishers speaking about their own interests](http://podcastalley.com). They will download straight to your PC as soon as they're published. You can listen to them on your PC or any portable MP3 player. If you have an IPod, programs like IPodder will push the downloaded MP3s straight into ITunes, so you can leave home each day with new content loaded on to your IPod. More info in <a href="http://podca.st">the Podcast FAQ</a></span>.

<h2>Quick Overview</h2>

Traditional webapps continue to send pages in their entirety, upon each user request. Consider a wiki such as [Wikipedia](http://wikipedia.org):

* User changes some text
* Browser submits the new text
* Server saves the text and sends the entire page again, updated this time
* Browser clears previous page and draws all of new page

**AJAX apps don't redraw the whole page. Instead, they send a little request, receive a result, and adjust the page accordingly.** The wiki of the future will look like this:

* User changes some text
* Browser submits the change
* Server saves the change and sends a confirmation and maybe the latest timestamp.
* Browser adjusts any information, e.g. shows the new timestamp.

For a glimpse of wikis to come, check out this [Instant Edit webapp](http://www.ideasfreelance.com/lab/instant_edit/). Fire it up in two different browsers and see how the changes persist without reloading the page.

**Most famously, Google has a few AJAX applications: [Google Maps](http://maps.google.com/), [GMail](http://gmail.com), [Google Suggest](http://www.google.com/webhp?complete=1&hl=en).**

<h2>YARC! Yet Another Rich Client!</h2>

**AJAX, and the underlying XMLHttpRequest object, is the latest approach in the tradition of enriching the web platform.** To put it into perspective, here are a few other attempts at rich applications over the years:

* In the early 1990s, the Mosaic browser made the web clickable. It was the first window-based browser.
* Images, then animations and sounds, were later added. ASCII art soon faded as quickly as silent film.
* Java allowed for client-side applets.
* Javascript (no relation) allowed for embedded programming inside HTML and led to a dramatic rise in cross-browser compatibility tables.
* Flash was introduced, and with Flash MX, became more programmer-friendly.
* Client-side GUI applications increasingly connected to the internet. e.g. Multiplayer games, Desktop search tools, ITunes Music Store, Auto-updating virus protection, Dreaded "free" spyware.
* Frames, and even better, invisible IFrames allowed for invisible request submission and manipulation of the current web page.
* Each browser continues to offer its own proprietary extensions (with some possible clicking of checkboxes or downloading of extra components): MS offers [.NET support](http://msdn.microsoft.com/netframework/programming/winforms/richclient.aspx), Mozilla and Firefox offer [a powerful plugin architecture](http://extensionroom.mozdev.org/), Opera offers a [presentation](http://www.opera.com/support/tutorials/operashow/) package.

<h2>The Heart of AJAX: XMLHttpRequest</h2>

**AJAX is a new name ([Feb 2005](http://www.adaptivepath.com/publications/essays/archives/000385.php)) for a design style that has been possible, and in fact used sparingly, for the past couple of years. The underlying technology is XMLHttpRequest, a Javascript object that supports web requests. Every big modern language has a class like this: it takes a URL, fetches the content, and provides query support. XMLHttpRequest supports standard text as well as XML documents. That means a web page can wait for Javascript events, submit info to a web server, catch the resulting output, and play around with the current page.**

One more thing about the technology: **the request-response cycle is asynchronous. The XMLHttpRequest object is registered with a response handling Javascript function, and fires off to the server. Some time later, the server probably comes back, and the registered function catches the result.** And that's what AJAX stands for: Asynchronous Javascript + XML.

Let's look at an example: [This chat application](http://www.plasticshore.com/projects/chat/index.html) is based on AJAX. You can see the Javascript [here](http://www.plasticshore.com/projects/chat/scripts.js). (The entire thing has a Creative Commons license.)

When the user says something, the function *sendComment()* is called. It grabs the user's message from the input field and passes it to httpSendChat, an XMLHtppRequest object. httpSendChat posts it to the server.
<pre> <code>
    httpSendChat.open("POST", SendChaturl, true);
    httpSendChat.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
    <i>httpSendChat.onreadystatechange = handlehHttpSendChat;</i>
    httpSendChat.send(param);
</code> </pre>

The emphasised line is the registration: it says that the response will come back to the *handlehHttpSendChat* function. That function will discard any partial responses, and upon receiving a full response (state=4), it will redraw the chat (which involves another trip to the server):

<pre><code>
function handlehHttpSendChat() {
  if (httpSendChat.readyState == 4) {
  	receiveChatText(); //refreshes the chat after a new comment has been added (this makes it more responsive)
  }
}
</code></pre>

*receiveChatText()* calls the server to send the recent discussion history, and ensures the response goes to handleHttpReceiveChat(). That function rearranges the chat text according to the recent message:

function handlehHttpReceiveChat() {
  if (httpReceiveChat.readyState == 4) {
    results = httpReceiveChat.responseText.split('---'); //the fields are separated by ---
    if (results.length > 2) {
	    for(i=0;i < (results.length-1);i=i+3) { //goes through the result one message at a time
	    	insertNewContent(results[i+1],results[i+2]); //inserts the new content into the page
	    }
	    lastID = results[results.length-4];
    }
     ....
  }

Great, it works if I say something. But it's a chat program. What if *someone else* says something? The application simply polls the server, ensuring that "receiveChatText" is called every four seconds.

## All About Usability

**The chief beneficiary of AJAX is the user. Web applications feel much more responsive, and the user won't hesitate to perform actions for fear of slow response times, or outright timeouts.** Furthermore, form data need not be lost due to browser crashes: using a timer, it can be sent to the server every few minutes, just like auto-backup.

For standard form-based applications, that's a nice benefit, but hardly a killer app. **Where AJAX will shine is in truely rich applications.** In particular, on intranets, where many corporations have already migrated traditional GUI applications. This migration process has usually been led by technologists concerned with the infrastructural overheads of administering and upgrading standalone applications. It's much easier to have all the applications sitting on the server and the clients running a standard web browser.

These web migrations may have improved administrability, but they have often cause users pain. Ironically, they're often left longing for applications written a decade before the web apps. It doesn't help that most projects are clueless with regard to usability, but even if usability is considered, the web platform is inherently unusable. The control components are simplistic and server synchronisation is confusing and time-consuming. AJAX doesn't do anything for the controls, but at least it brings the server and client closer together. 

## Problems with AJAX

Some objections are taken from the resources below, especially [AJAX: Promise or Hype](http://www.quirksmode.org/blog/archives/2005/03/ajax_promise_or.html).

###It's Hard to Code
Any Javascript usually makes life more difficult, and early discussions indicate AJAX is no different. **At present, coding for AJAX may well be more difficult, although if you look at the code examples around, you'll see that you're not exactly facing a Turing Test either. In any event, it's inevitable that design patterns and supportive frameworks will emerge.** A few frameworks already facilitate this mode of development: the always-controversial, uber-funky [Ruby On Rails](http://weblog.rubyonrails.com/archives/2005/03/27/rails-0111-more-ajax-verifications-sql-server-updated-loads-of-fixes/), 
[JSON-RPC-Java](http://oss.metaparadigm.com/jsonrpc/), [Dynamic Web Remoting](http://eireneh.thorubio.org/dwr/).
[SAJAX](http://www.modernmethod.com/sajax/), [Echo 2](http://www.theserverside.com/news/thread.tss?thread_id=32834). Fortunately for evolution, a wide variety of approaches is being taken. Cross-fertilisation will undoubtedly follow.

In particular, the best frameworks will probably generate as much Javascript as possible, so developers don't need to co-ordinate between Javascript and server-side controllers.

### Testability May Suffer
It's nice to be able to perform system tests with a robot like httpUnit. Any use of Javascript makes that more difficult. At the same time, because AJAX promotes a more component-based architecture, unit testing may actually be improved. With a good design, it should be quite feasible to test the scripts that are accessed by the XMLHttpRequest object.

### Accessibility May Suffer
Any form of interactivity is often anathema to many different types of specialised needs. Nevertheless, this should not stop the technology from progressing, and providing rich interaction to those who can use it. As always, accessibility must be maintained, and multiple mechanisms might be required. Furthermore, new technologies can improve accessibility too. It's easy to imagine, for example, how an AJAX-enabled site could let users quickly resize and move around certain screen elements to meet their individual needs.

### AJAX Will Collapse the Network

AJAX does represent a potential challenge to networking infrastructure. Traditional web applications can feel like earlier client-server applications. Submit your offerings, then receive a response and meditate on it for a while. AJAX makes the term "web application" a lot more honest. The server really is involved, possibly even after each keystroke. Interestingly, bandwidth requirements may go down because usually only small changes need to be sent each way. However, latency is another question: using an AJAX application might feel like typing against a slow telnet connection. Stuff... hap...pens...much...sl..ower...than you...can...think... .

This will probably not be a major concern on intranets, where there are relatively few users and usually good connectivity to the server (especially as it's often nearby). However, it's still an open question how AJAX will be used on the public web. Certainly, it can be used to incrementally improve just about any form-based application. And it can surely go beyond that, as Google demonstrates. But can it scale to the requirements of a major site, offering a fully-scaleable wiki or genuinely playable gaming?

### It's Just a Name, the Tech's Not New At All
XMLHttpObject has been around for a few years, but it would be hard to believe anything called "XMLHttpObject" could trigger a revolution on the PCs of the world. Frames and IFrames supported this sort of interaction even earlier. **History and logic would suggest that a standard name and community, combined with some flagship applications, are powerful tools indeed.** And the timing is right: users have lived with static web applications long enough, broadband is now mainstream, and the economy hungers for innovation. The raw technology may have been around, and even used in doses. **But all signs indicate that the new name, given the increased need and the prominent offerings by Google offerings, constitutes a [tipping point](http://www.gladwell.com/tippingpoint/)**.

### Bill Won't Like It
Let's be clear. This could have happened a lot earlier. There's a lot of unfounded nonsense about MS on the web, but there is indeed broad agreement that MS does not benefit from adoption of rich web applications. And for pretty obvious reasons. They worked hard to innovate with IE in the mid-90s, attaining the dominant position.  Consequently, they managed to crush Netscape's dreams of replacing the Office Suite and Sun's dreams of Java on every desktop. It's hard to see MS doing anything about XMLHttpRequest within IE though; the interaction it provides is rich, but quite frankly, not *that* rich.

### Flash Can Do All This, and More
Flash is a bit of a mystery, since it's extremely cross-platform, having excellent support on all the major browsers and platforms. And yet, it's never taken off for serious application work. In fact, it's really been used for not much more than ads and fancy presentations. It's certainly capable of doing much more serious applications, and maybe Flash MX will still shine. It took a long time for Macromedia to target serious development. Perhaps this was a strategic mistake, or perhaps it was an intentional means of gaining wide browser share. 

##Examples

* [Working AJAX Examples](http://www.fiftyfoureleven.com/resources/programming/xmlhttprequest/examples#L-319)
* [Google Maps](http://maps.google.com/). Analysis: [http://jgwebber.blogspot.com/2005/02/mapping-google.html]
* [Instant Editor](http://www.ideasfreelance.com/lab/instant_edit/)

##Further Resources

* [Ajax: A New Approach to Web Applications](http://www.adaptivepath.com/publications/essays/archives/000385.php) is the Feb-18-2005 article which introduced the "AJAX" name.
* [AJAX: Promise or Hype](http://www.quirksmode.org/blog/archives/2005/03/ajax_promise_or.html) examines the community fallout from the original article.
* [Ajaxian](http://www.ajaxian.com/) is a new blog by [Dion Altmar](http://www.almaer.com/blog/) and [Ben Galbraith](http://www.galbraiths.org/).
* [AJAX discussion on TheServerSide.net](http://www.theserverside.net/news/thread.tss?thread_id=32688)