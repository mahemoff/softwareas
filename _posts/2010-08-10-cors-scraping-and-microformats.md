---
id: 942
title: CORS, Scraping, and Microformats
date: 2010-08-10T12:42:16+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=942
permalink: /cors-scraping-and-microformats/
dsq_thread_id:
  - "375259288"
categories:
  - SoftwareDev
tags:
  - Ajax
  - html5
  - Javascript
  - Microformats
  - Web Services
  - XMLHttpRequest
---
 <a href="https://dl.dropbox.com/u/8429420/experiment/hcard/index.html">Jump straight to the demo.</a>

<a href="http://www.w3.org/TR/2010/WD-cors-20100727/">Cross-Origin Resource Sharing</a> makes it possible to do arbitrary calls from a web page to any server, if the server consents.  It's a typical HTML5 play: We could do similar things before, but they were with hacks like JSONP. Cross-Origin Resource Sharing lets us can achieve more and do it cleanly. (The same could be said of Canvas/SVG vs drawing with CSS; WebSocket vs XHR-powered Comet; WebWorker vs yielding with setTimeout; Round corners vs 27 different workarounds; and we could go on.)

This has been available for a couple of years now, but I don't see people using it. Well, I haven't checked, but I don't get the impression many sites are offering their content to external websites, despite social media consultants urging them to be "part of the conversation". It's like when people make a gorgeous iPhone app, but their website doesn't work at all in the same phone  (*cough* <a href="http://www.cloudfour.com/iphone-app-store-blinders/">fashionhouse</a>) . Likewise, if you've got a public API, but not providing JSONP/callback support, it's not very useful either...making developers host their own cross-domain proxy is tedious. It's cool there are services like YQL and Embed.ly for some cases, but wouldn't it be better if web pages could just pull in all that external content directly?

Except in this case, it's just not happening. Everyone's offering APIs, but no-ones sharing their content through the web itself. At this point, I should remind you I haven't actually tested my assumption and maybe everyone is serving their public content with "Access-Control-Allow-Origin: *" ... but based on the lack of conversation, I am guessing in the negative. The state of the universe does need further investigation.

Anyway, what's cool about this is you can treat the web as an API. <strong>The Web is my API.</strong> "Scraping a web page" may sound dirtier than "consuming a web service", but it's the cleaner approach in principle. A website sitting in your browser is a perfectly human-readable depiction of a resource your program can get hold of, so it's an API that's self-documenting. The best kind of API. But a whole HTML document is a lot to chew on, so we need to make sure it's structured nicely, and that's where <a href="http://microformats.org">microformats</a> come in, gloriously defining lightweight standards for declaring info in your web page. There's another HTML5 tie-in here, because we now have a similar concept in the standard, <a href="http://diveintohtml5.org/extensibility.html">microdata</a>.

<a href="https://dl.dropbox.com/u/8429420/experiment/hcard/index.html">So here's my demo.</a>

I went to my homepage at <a href="http://mahemoff.com">mahemoff.com</a>, which is spewed out by a PHP script. I added the following line to the top of the PHP file:
[php]
<?
  header("Access-Control-Allow-Origin: *");
  ... // the rest of my script
?>
[/php]

Now any web page can pull down "http://mahemoff.com/" with a cross-domain XMLHttpRequest. This is fine for a public web page, but something you should be very careful about if the content is (a) not public; or (b) public but dependent on who's viewing it, because XHR now has a "withCredentials" field that will cause cookies to be passed if it's on. A malicious third-party script could create XHR, set withCredentials to true, and access your site with the user's full credentials. Same situation as we've always had with JSONP, which should also only be used for public data, but now we can be more nuanced (e.g. you <em>can</em> allow trusted sites to do this kind of thing).

On to the client ...

I started out doing a standard XHR, for sanity's sake.

<img src="http://farm5.static.flickr.com/4095/4878985954_35f74aa1ea.jpg" />

[javascript]

  var xhr = new XMLHttpRequest();
  xhr.open("get", "message.html", true);
  xhr.onload = function() { //instead of onreadystatechange
    if (xhr.readyState==4 && xhr.status==200)
    document.querySelector("#sameDomain").innerHTML = xhr.responseText;
  };
  xhr.send(null);
[/javascript]

Then it gets interesting. The web app makes a cross-domain call using the following facade, which I adapted from a snippet in the veritable Nick Zakas's <a href="http://www.nczonline.net/blog/2010/05/25/cross-domain-ajax-with-cross-origin-resource-sharing/">CORS article</a>:
[javascript]
function get(url, onload) {
    var xhr = new XMLHttpRequest();
    if ("withCredentials" in xhr){
      xhr.open("get", url, true);
    } else if (typeof XDomainRequest != "undefined"){
      xhr = new XDomainRequest();
      xhr.open("get", url);
    } else {
      xhr = null;
    }
    if (xhr) {
      xhr.onload = function() { onload(xhr); }
      xhr.send();
    }
    return xhr;
}
[/javascript]

This gives us a cross-domain XHR, for any browser that supports the concept, and it makes a request the usual way, and the request works against my site, but not yours, because of the header I set earlier on my site. Now I can dump that external content in a div:

<img src="http://farm5.static.flickr.com/4114/4878413271_d09c4f2497_z.jpg" />

[javascript]
  get("http://mahemoff.com/", function(xhr) {
    document.querySelector("#crossDomain").innerHTML = xhr.responseText;
    ...
[/javascript]

(This would be a monumentally thick thing to do if you didn't trust the source, as it could contain script tags with malicious content, or a phishing form. Normally, you'd want to sanitise or parse the content first. In any event, I'm only showing the whole thing here for demo purposes.)

Now comes the fun part: Parsing the content that came back from an external domain. It so happens that I have embedded hCard microformat content at http://mahemoff.com. It's in the expandable business card you see on the top-left:

<a href="http://mahemoff.com"><img src="http://farm5.static.flickr.com/4136/4878996726_cc4ebbf185_t.jpg"></a>

And the hCard content looks like this, based on :

[html]
<div id="card" class="vcard">
  <div class="fn">Michael&nbsp;Mahemoff</div> 
  <img class="photo" src="http://mahemoff.com/speak2.jpg"></img>
  <div class="role">"I like to make the web better and sushi"</div>
  <div class="adr">London, UK</div> 
  <div class="geo">
    <abbr class="latitude" title="51.32">51&deg;32&#39;N</abbr>,     <abbr class="longitude" title="0">0&deg;</abbr>
  </div>  <div class="email">michael@mahemoff.com</div>
  <div class="vcardlinks">    <a rel="me" class="url" href="http://mahemoff.com">homepage</a>
    <a rel="me" class="url" href="http://twitter.com/mahmoff">twitter</a>    <a rel="me" class="url" href="http://plancast.com/mahemoff">plancast</a>
  </div>
</div> 
[/html]

It's based on the <a href="http://microformats.org/wiki/hcard">hCard microformat</a>, which really just tells you what to call your CSS classes...I told you microformats were lightweight! The whole idea of the card comes from Paul Downey's genius <a href="http://blog.whatfettle.com/2010/01/14/hardboiled-hcards/">Hardboiled hCards</a> project.

Anyway, bottom line is we've just extracted some content with hCard data in it, so it should be easy to parse it in a standard way and make sense of the content. So I start looking for a hCard Javascript library and find one, that's the beauty of standards. Even better, it's called <a href="http://www.danwebb.net/2007/2/9/sumo-a-generic-microformats-parser-for-javascript">Sumo</a> and it comes from Dan Webb.

The hCard library expects a DOM element containing the hCard(s), so I pluck that from the content I've just inserted on the page, and pass that to the library. Then it's a matter of using the "hCard" object to render a custom UI:

<img src="http://farm5.static.flickr.com/4078/4879071706_806f389a5b.jpg">

[javascript]
    var hcard = HCard.discover(document.querySelector("#crossDomain"))[0];
 var latlong = new google.maps.LatLng(parseInt(hcard.geo.latitude), parseInt(hcard.geo.longitude));
  var markerImage = new google.maps.MarkerImage(hcard.photoList[0], null, null, null, new google.maps.Size(40, 40));
 var infoWindow = new google.maps.InfoWindow({content: "<a href='"+hcard.urlList[0]+"'>"+hcard.fn+"</a>", pixelOffset: new google.maps.Size(0,-20)});
   ...
[/javascript]

And I also dump the entire hCard for demo purposes, using James Padolsey's <a href="http://james.padolsey.com/javascript/prettyprint-for-javascript/">PrettyPrint</a>.

<img src="http://farm5.static.flickr.com/4123/4879071986_45ab3ce235.jpg">

[javascript]
document.querySelector("#hcardInfo").appendChild(prettyPrint(hcard));
[/javascript]

There's lots more fun to be had with the Web as an API. According to <a href="http://microformats.org/">the microformats blog</a>, 2 million web pages now have embedded hCards. Offer that content to the HTML5 mashers of the world and they will make beautiful things.