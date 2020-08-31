---
id: 492
title: 'Offline Sound: No Flash, No File'
date: 2008-10-21T23:08:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=489
permalink: /offline-sound-no-flash-no-file/
dsq_thread_id:
  - "375522458"
categories:
  - SoftwareDev
tags:
  - Ajax
  - AjaxPatterns
  - Flash
  - Javascript
  - Sound
  - TiddlyWiki
  - Web
---
I just did some tinkering with offline sound and it turns out you can embed an audio clip in an HTML file, and play it without using Flash. I could have demo'd this in a raw HTML file, but it was just as easy to stick it in a Tiddlywiki file. So I made <a href="http://mahemoff.com/project/tiddlywiki/jinglywiki.html">a TiddlyWiki called JinglyWiki</a>. Click on the button and it will play a sound. If you grab the file (safest using a tool like Curl or wget, as the browser will sometimes Save As something different), you can run it offline and it will still play the sound.

<a href="http://mahemoff.com/project/tiddlywiki/jinglywiki.html"><img style="width: 98%; border: 1px solid black;" src="http://picupper.com/2008/10/21/jingly.png"></a>

<a class="tiddlyLink tiddlyLinkExisting" href="javascript:;" title="JinglyWiki - Mahemoff, Tue Oct 21 23:11:00 2008" refresh="link" tiddlylink="JinglyWiki">JinglyWiki</a> started after an office conversation yesterday. We had a flaky wifi connection and were pleased to be able to play a beat on <a class="externalLink" href="http://instantrimshot.com" title="External link to http://instantrimshot.com" target="_blank">http://instantrimshot.com</a> to signify a re-connection. This got us thinking about playing beats in Tiddlywiki. <a class="externalLink" href="http://jermolene.com/" title="External link to http://jermolene.com/" target="_blank">Jeremy</a> mentioned the possibility of data: URIs, and I thought back to <a class="externalLink" href="http://www.zwitserloot.com/files/soundkit/soundcheck.html" title="External link to http://www.zwitserloot.com/files/soundkit/soundcheck.html" target="_blank">Reinier's great effort in playing sound without Flash</a>. I wondered if it would work with data: URIs and to my pleasant surprise, it did. At least in FF3, which is all I've tested so far. I also forgot how tiny the code is to play audio without Flash - you just add an element to the page.
<br/>
<br/>
The point of JinglyWiki is you can stick a 300K file on your local file system or a USB stick and play gratuitous sounds without being online. Your iPod cost you several hundred bucks, whereas JinglyWiki is entirely free. Free as in you can spend your money on beer instead. JinglyWiki may well be the best portable music player you never paid a penny for. Groovy.
<br/>
<br/>
It would be so much more useful with some code to dynamically generate WAVs, but that's a project for another day.
<br/>
<br/>
As for the name, it's a play on the much more important project Phil Hawksworth has initiated to build a JQuery
based Tiddlywiki framework: <a class="externalLink" href="http://jigglywiki.com" title="External link to jigglywiki.com" target="_blank">JigglyWiki</a>. I think this nascent effort is going to produce some wonderful plugins for the JQuery community and be an important enough project to derive novelty joke names out of :), so I'm setting the trend here.

The data itself is 15KB for about a second of voice content.

Here's the plugin code. Trivial or wot?!!!

[javascript]
config.macros.jingle = {}
config.macros.jingle.handler = function(place,macroName,params,wikifier,paramString,tiddler) {

  button = document.createElement("button");
  button.style.fontSize = "4em";
  button.innerHTML = "Play Me! Play Me!"
  button.onclick = function(ev) {
    startWav(SOUND_URL);
  }
  place.appendChild(button);

  // cancel dbl-click so we can follow our natural urge to click on the button incessantly
  story.getTiddler(tiddler.title).ondblclick = function() {}

}

// non-flash sound handling adapted from http://www.zwitserloot.com/files/soundkit/soundcheck.html

var embedEl;

function startWav(uri) {
        stopWav();
        embedEl = document.createElement("embed");
        embedEl.setAttribute("src", uri);
        embedEl.setAttribute("hidden", true);
        embedEl.setAttribute("autostart", true);
        document.body.appendChild(embedEl);
}

function stopWav() {
  if (embedEl) document.body.removeChild(embedEl);
  embedEl = null;
}

// To make a new sound, cut and paste into hixie's handy Data URI Kitchen
// http://software.hixie.ch/utilities/cgi/data/data.pl

var SOUND_URL="data:audio/x-wav,RIFF%17%1C%00%00WAVEfmt%20%10%00%00%00%01%00%01%00%40%1F%00%00%40 ........................" // snipped
[/javascript]