---
id: 1067
title: Is this what the App of 2015 looks like? HTML5 + CoffeeScript + Less + WebStore + PhoneGap + Apparatio
date: 2011-01-10T18:32:58+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1067
permalink: /is-this-what-the-app-of-2015-looks-like-html5-coffeescript-less-webstore-phonegap-apparatio/
dsq_thread_id:
  - "375146888"
categories:
  - SoftwareDev
tags:
  - CoffeeScript
  - CSS
  - html5
  - Javascript
  - Less
  - Project
---
<a href="http://project.mahemoff.com/hn"><img src="http://posterous.com/getfile/files.posterous.com/mahemoff/vPWTFXR5SPm7QWzKDIFbkGoTzWzoU60fxzIuVIDsekmy8UfqdYQ1W3u8O9ZI/photo.png.scaled.1000.jpg" /></a>

My weekend project was a <a href="http://project.mahemoff.com/hn">Hacker News Reader</a> (<a href="https://github.com/mahemoff/hackernews">source code</a>). It works on Chrome, Safari, and Opera. Sorry, Firefox doesn't work at present, reasons why speculated below. Mostly started this project because I want one with Twitter integration, but also to play with a few technologies, which I did. Among things explored and demonstrated:
<ul>
  <li><strong>Server-Less App</strong> The app is entirely browser-side. The server serves only as a repository of static files. Content comes from the iHackerNews unofficial API, by way of JSONP, the protocol we'll still use for cross-domain calls until CORS becomes eminent in the hopefully not-too-distant future.</li>
  <li><strong>CoffeeScript.</strong> The app logic is written in <a href="http://jashkenas.github.com/coffee-script/">CoffeeScript</a>, and compiled to JavaScript in the browser with coffee-script.js.</li>
  <li><strong>Less.</strong> The UI styling is written in <a href="http://lesscss.org/">Less</a> and compiled to CSS with <a href="https://github.com/cloudhead/less.js/">less.js</a>.</li>
  <li><strong>Chrome Web App.</strong> The app is also a <a href="https://chrome.google.com/webstore/detail/npalbnjnpgfknopcnjofihcankbnngef">hosted web app</a> on the <a href="https://chrome.google.com/webstore">Chrome Web Store</a>, which is to say (a) it can be discovered by users of the store; (b) it can be installed into the New Tab page of Chrome, for convenience sake; (c) if I wanted to, and added some extra server smarts, I could charge for it. I wrapped it up as an app with <a href="http://paul.kinlan.me">Paul's</a> super-handy <a href="http://appmator.appspot.com">Appmator</a> utility.</li>
  <li><strong>Mobile HTML5.</strong> Although I didn't (yet) optimise the site for HTML5, I did make it available on mobile, with the right icons for being added to the Home Page, and used Build.PhoneGap.com and Apparatio to roll it up as a native mobile app.</li>
</ul>

<h3>CoffeeScript</h3>

<a href="http://jashkenas.github.com/coffee-script/"><img src="http://farm6.static.flickr.com/5043/5341566290_f25af808f2_o.jpg" /></a>

I wanted to try out CoffeeScript. While I've been skeptical about languages which are said to "compile down" to JavaScript, as if JavaScript was a complicated tangle of 1s and 0s rather than the high-level language it is...CoffeeScript is different. It's more like JavaScript++ as the name implies. While I do find JavaScript to be pretty good, its syntax can get too verbose. Especially for closures, where you have too many curly braces and "function" keywords getting in the way of the actual logic we care about. You can also be more expressive with keywords like "unless".

As ~98% of code people write never sees high-scale production use, I like to opt for quick and dynamic over tedious and "it just feels like the right way to do it". So I employed coffee-script.js to compile dynamically, in the browser when the web app loads, instead of pre-compiling it on the command-line. Doing it dynamically means I can just type some code and reload the browser page, about the smallest possible debug-test cycle that is possible.

I found it slow-going at first, because I ran into some coffee-script.js gotchas and learned a few things about the language on the way:

<ul>
  <li>Keep CoffeeScript in a separate server. Although CoffeeScript supports inline CoffeeScripts in your HTML (&lt;script type="text/coffeescript"&gt;...here is my script....&lt;/script&gt;) - perfect for quick hacking), I recommend you stick them in a separate file (&lt;script type="text/coffeescript" src="myscript.coffee"&gt;&lt;/script&gt;. I can't explain exactly why, but when it was inline, things were note very deterministic and I found my CoffeeScript script was getting executed three times!</li>
  <li>Use a server, not file:/// URIs. As with less.js, CoffeeScript mocks the browser's script-downloading behaviour, using XMLHttpRequest to pull down any scripts specified in "text/coffeescript" script tags. Unforuntately, Chrome doesn't let you XHR one file from another file, so you need to set up a server, if only to serve these static files over HTTP.</li>
  <li>Don't bother with window.onload (or jQuery intializer). I *think* coffee-script.js guarantees any CoffeeScripts you provide will be executed after the window has already loaded. I haven't confirmed this, but seems to be that way on Chrome, Safari, and Opera. OTOH, the app doesn't work on Firefox - CoffeeScript isn't executed at all - and this may be related.</li>
  <li>Declare before you use. A consequence of the previous rule is that your initialisation sequence will run in the order you specify it. This is different to the usual JS situation where you make a window.onload handler, which might call things that you've declared further down in the file. So in the code further down, note that I declare "show" before I call it. Pretty obvious, but JS habits and lack of descriptive error messages meant it caught me out.</li>
  <li>Whitespace matters. There are no semi-colons and no braces here; similar to Python, whitespace dictates structure. However, you can also use parantheses to keep things on the same line, so I didn't find this threatening to concise code.</li>
  <li>Use "window" for global. Declarations like "x=5" out in the open will *not* make global variables; and nor is there a "var" keyword. The only way to hook into global space is to explicitly reference the "window" object; e.g. "window.x = 5".</li>
</ul>

How's the code look? <a href="https://github.com/mahemoff/hackernews">See for yourself</a>, CoffeeScript keeps it pretty tight. I couldn't find many examples of jQuery-CoffeeScript combos, so this will hopefully be useful in that regard:

[javascript]
storiesTemplate = _.template($("#storiesTemplate").html())
show = () ->
  $.getJSON "http://api.ihackernews.com/page?format=jsonp&callback=?",
    (storyInfo) -> $("#stories").fadeOut () ->
      $(this).html(storiesTemplate(storyInfo))
      $(this).fadeIn()

show()
setInterval show, 10*60*1000

$(".story").live "click", (ev) -> 
  return if $(ev.target).closest("a").length
  window.open($(".url", this).attr("href"), "hackernews"+Math.random());
[/javascript]

<ul>
  <li>Less fails silently. Unfotunately, you don't get error messages, so develop things gradually and be prepared to undo.</li>
</ul>

<h3>Less</h3>

<a href="http://lesscss.org"><img src="http://farm6.static.flickr.com/5245/5343036433_fe9692faea_o.jpg"/></a>

If I was going to take a sip of CoffeeScript, it would only be fair to munch on a slice of Less too. If CoffeeScript is JavaScript++, then Less is CSS+. It's really augmented CSS, because you can present a regular CSS stylesheet and it will be valid Less too. That's not true at all about CoffeeScript; a typical JavaScript script has Buckley's of passing the CoffeeScript compiler.

The other thing they have in common is JavaScript compilers. Which is not the case with <a href="http://sass-lang.com/">SASS</a> for instance.

Less talk:

<ul>
  <li>Same XHR issues. As with CoffeeScript, the Chrome cross-domain restriction means you have to use a server even though the files are static. Also, it doesn't seem to be possible to include Less stylesheets inline, or to get hold of the less compiler, which I think is a shame if true.</li>
  <li>Silent fail. If any Less doesn't parse, the entire stylesheet won't be applied, and there's no error message.</li>
</ul>

So some downsides, but the upside was a cleaner stylesheet with less redundancy. Gradient macro makes the ridiculously verbose gradient declarations completely DRY:

[css]
/*****************************************************************************
   MACROS
*****************************************************************************/
.linearGradient(@color1:#ccc, @color2:#ddd) {
  background-image:-webkit-gradient(linear, left bottom, left top, color-stop(0, @color1), color-stop(100%, @color2));
  background-image:-moz-linear-gradient(center bottom, @color1 0, @color2 100%);
  background-image:-o-linear-gradient(center bottom, @color1 0, @color2 100%);
  background-image:linear-gradient(center bottom, @color1 0, @color2 100%);
  background-color: @color1;
}
.postedBy:hover, .commentsLink:hover span { .linearGradient(#fa0, #f80); }
[/css]

Elements can be nested in their parent selectors:

[css]
.commentsLink,.commentsLink:visited {
  position: absolute; top: 50%; right: 1em; height: 1em;
  ...

  span {
    ...
    border-radius: 0.3em;
  }

}
[/css]

... and so can pseudo-selectors:
[css]
.story { 
  padding: 0.5em 9em 0.5em @leftIndent;
  border: 1px solid black;  border-bottom-width: 0;
  background: #fff6f6;  cursor: pointer;
  position: relative;

  &:hover { .linearGradient(#fc0, #fa0); }

  &:last-child { border-bottom-width: 1px; }
   
}
[/css]

And you can do cross-browser <a href="http://singy.posterous.com/firefox-4-css3-calc">CSS calculations</a> today:

[css]
.commentsLink,.commentsLink:visited {
   ...
  margin-top: -0.5em-@commentsLinkPadding;

  span {
    ...
    padding: 0em + @commentsLinkPadding;
  }

}
[/css]

<h3>Chrome Web Store</h3>

This is a full-screen, focused, app which therefore meets the criteria for Web Apps I outlined in <a href="http://code.google.com/chrome/apps/articles/thinking_in_web_apps.html">Thinking In Web Apps</a>. (It would be more so if it showed the actual stories and comments in the app too, but that's something for later.)

So it made sense to submit to the Chrome Web Store. Fortunately, my colleague <a href="http://paul.kinlan.me">Paul Kinlan</a> had the gall to attempt building a web app that packages up Chrome apps ... and then he actually pulled it off! <a href="http://appmator.appspot.com">Appmator</a> asks you for the address of your web app, asks a few other basic questions, and then makes a Zip file you can drag to your desktop and upload to the store. All in all, a 30 minute submission to the Chrome Web Store and a nice way for people to discover your web app. I would only recommend this for true "Apps" as opposed to general websites, and ideally those apps should be tailored to a full-screen experience.

<a href="http://appmator.appspot.com"><img src="http://farm6.static.flickr.com/5002/5341112662_b389ba96ef_o.jpg" /></a>

Anyway, it's on the store now - <a href="https://chrome.google.com/webstore/detail/npalbnjnpgfknopcnjofihcankbnngef">Hacker News landing page</a>.

<img src="http://farm6.static.flickr.com/5043/5342682311_b6bb5e5536_o.jpg" />

<h3>PhoneGap, PhoneGap Build, Apparatio</h3>

The app is *NOT* optimised for mobile at this time, but the cool thing about HTML5 is, for the most part, it "just worked" when I pointed iPad and Android phones to it. Some things need improvement, but this is good to see.

For exploration purposes, I decided to build it as a native mobile app anyway.  I was lucky enough to receive beta invites for PhoneGap Build and Apparatio, two web services which let you do PhoneGap without actually installing anything on your PC. I built this app with both products.

Apparatio, which I <a href="http://mini.softwareas.com/first-impressions-of-apparatio">used previously</a>, worked nicely and I was able to get a <a href="http://apparat.io/preview/static/package/2011/01/09/Hacker_News_0.1-debug.apk">native Android app</a>.

PhoneGap Build supports GitHub like Apparatio, but also allows uploading a zip file. I actually had a problem pointing it at my GitHub repo (as with Apparatio, it needs to provide clearer instructions on exactly what form of URL is required). After I uploaded the zip file, it showed me a dashboard of 4 packages being built, and just went ahead and built each of them. Nice and simple!

<img src="http://farm6.static.flickr.com/5168/5340759715_f5e6a82af9_z.jpg" />

Android, WebOS, Symbian, Nokia. Conspicuous by its absence is iOS, which Apparatio does support.

DropBox on my Macbook and Galaxy made it easy to copy the APK downloads to my Galaxy and install it. The Apparatio one took some time to download initially, but worked fine. The 

<h3>Other Notes</h3>

<strong>Block-level "a" element, NOT.</strong> HTML5 makes it possible for "a" elements to be block-level, i.e. to include other tags including other "a" elements. This would be ideal for the Hacker News Reader UI, where the entire story block is a link to the story itself, but the block also contains links to comments and authors. It turned out to be legal in modern browsers, but with blatantly wrong layout, as <a href="http://www.onderhond.com/blog/work/nesting-links-how-to-make-your-browser-v">someone else found earlier</a>. Shame as I had to introduce considerably more <s>JavaScript</s>CoffeeScript and <s>CSS</s>Less.

<strong>InnerHTML, Templating, and Live().</strong> Seems like every project I do these days, I'm building dynamic content with innerHTML, as opposed to DOM manipulation. The first reason is I've become accustomed and satisfied with templating, and see it as a growing trend thanks to language-agnostic formats like Mustache as well as server-side JavaScript. (Though in this case, it's a pure browser-side app.) So make a template and stick it on the page with innerHTML (or jQuery's .html() ). The second reason is jQuery's live() command makes it easy to handle events against the newly formed elements, which was previously a pain with innerHTML(). 

<strong>Setting text size.</strong> As you can see, text size varies with the number of points a story has. The relevant line appears in the template:

<tt>font-size:&lt;%= Math.log(Math.log(Math.max(s.points,10))) %&gt;em;</tt>

Using a log scale ensures a story with 2000 points isn't 2000 times bigger than a story with 2 points. To dampen the effect further, which I think is important in mobile displays, I used a double-log and applied a minimum threshold of 10 points.

<h3>Future Things</h3>

There was actually an itch to be scratched here, beyond trying out  various tech. Specifically, I've been wanting a mobile HN reader that would: (a) tweet; (b) *quickly* mark for instapaper reading, and ideally when I'm offline. (It would show the latest stories it saw when online, and cue them up for later...in general, I wish more offline apps would support cueing things like Tweets and Read Laters for when you're back online.)

Fin.

<h3>So is this the Web App of 2015 or not?</h3>

There are definitely elements here that are not in wide use now, but will be in wide use by 2015. The whole "write once, run many" aspect of HTML5 is just getting wheels. It's now clear that Apple won't dominate the landscape by 2015, so regardless of their ever-fluctuating stance, HTML5 will be able to power the apps of the majority of smartphones and tablets...not to mention the possibility of apps on TV, cars, watches, washing machines, etc etc etc. (Can you tell it's been CES week?)

And with HTML5 being able to power these apps, we'll need ways to fit them into the App ecosystem, and that's where PhoneGap and friends fit in. As I've said in various places, I always found it painful to have to set up Eclipse, PhoneGap SDK, and so on just to make a native app from HTML5. These are the things HTML5 developers don't want to do, and the PhoneGap team is well aware of it, hence their PhoneGap Build effort. Apparatio provides relief in the same way and we can expect the same from others, especially so in light of Heroku's high-valuation acquisition bringing attention to the whole idea of <a href="http://softwareas.com/uml-tools-in-the-cloud">cloud programming</a>. GitHub is also a vital component of this vision becoming reality. The next step will be to automate deployment into the stores, hopefully something that app-hungry stores will be happy to facilitate.

The Chrome Web Store is a related concept aiming to "app-ize" we apps. Mozilla is investigating a similar idea, and we'll see a lot more of it in the next few years too. Some people say "but it's just a bookmark", an understandable reaction, but I think people are starting to get it now. It should only be an app if it really is an app, ie. if the underlying URL is really a media-rich, focused, app rather than a big collection of information and hyperlinks. And the Web Store is not just a place where you can buy and install apps; it's also a directory where you can find all the cool apps on the web, with screenshots and reviews and comments to help you decide if they're worth trying out.

Offline is important in the app story too (although this app doesn't (yet) do any offline). You don't type in URLs when you're on a plane, but you do click on app icons to launch them. So offline web apps need an app-like presence to meet user expectations.

How about those languages, CoffeeScript and Less? CoffeeScript seems promising and I'll definitely be using it more. At the same time, I'm weary because I feel like JavaScript may be "good enough" and CoffeeScript becomes a maintenance problem if others need to see your code. But the leap is not a big one.

As for Less, I'm more convinced it's the way to go. We nowadays have an absurd proliferation of "-webkit-" "-moz-" "-o-" "-msie-" prefixes and the various syntaxes to go with them. It's for good reason, but it's also as much an affront to the DRY principle as any agilist could ever fear, and it's unfortunate the standards don't provide better support for dealing with this sort of thing. Likewise, the need for variables/constants and calculations. Less allows for all of that, and in a way that will work on legacy browsers even when some of these features do come about. So, yes, I'll be committing to Less in the future.

What's very cool about both Less and CoffeeScript is the JavaScript frameworks. It's ideal for starting off a project, and when performance gets to be an issue, you can easily switch to the compiled version after that.

Finally, I'll mention that templating is a design pattern that's also going to be big in 2015. There's much more framework support these days and it's easy to use <a href="http://softwareas.com/dual-side-templating">the same templates</a> on the browser and the server.