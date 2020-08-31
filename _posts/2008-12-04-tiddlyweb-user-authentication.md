---
id: 500
title: TiddlyWeb user authentication
date: 2008-12-04T12:59:53+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=497
permalink: /tiddlyweb-user-authentication/
dsq_thread_id:
  - "375574065"
categories:
  - SoftwareDev
tags:
  - tiddlyweb
  - TiddlyWiki
---
I've been getting to grips with TiddlyWeb  and authentication lately. 

The following plugin code will set the username in the TiddlyWiki client to match the username that was presented to the server. It's simply a one-liner which delegates to <a href="http://www.quirksmode.org/js/cookies.html">quirksmodes' cookie handling library</a>. This all assumes tiddlyweb is using the authentication challenger, as there's no standard on cookie names.

[javascript]
config.options.txtUserName = readCookie("tiddlyweb_user").split(":")[0].substr(1);

// http://www.quirksmode.org/js/cookies.html
function readCookie(name) {
  var nameEQ = name + "=";
  var ca = document.cookie.split(';');
  for(var i=0;i < ca.length;i++) {
    var c = ca[i];
    while (c.charAt(0)==' ') c = c.substring(1,c.length);
    if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
  }
  return null;
}
[/javascript]

BTW this isn't essential. When a user uploads something, TiddlyWeb will automatically set the modifier to the username on the server anyway. So the next time the user sees it, it will have the right username anyway. But having the right username in the client will make things right from the start and it feels cleaner to upload the tiddler with the right username data, even if it's ignored. I could imagine future versions/plugins on the server that allow any username to be uploaded, with some algorithm to check if it's allowed. (ie if admin, allow all usernames.)