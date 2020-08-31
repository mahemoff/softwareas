---
id: 1918
title: JavaScript swims downstream with the web
date: 2013-04-19T00:49:41+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1918
permalink: /javascript-swims-downstream-with-the-web/
categories:
  - SoftwareDev
---
Roy Fielding's original REST dissertation (published in 2000) has an interesting section on Java versus JavaScript, which I've not come across before and has certainly stood the test of time. In particular, the biggest benefit is explained to be nothing more complicated than performance, obviously a huge deal these days.

Extract below with obligatory [PSD artwork](http://www.flickr.com/photos/psd/421186578/). Emphasis mine.

[Background: Speaking about [REST at Web Directions Code](http://code13melb.webdirections.org/) soon and finding myself on a long day of interstate flights, I bit the bullet and finally read [Roy Fieldings' original REST thesis](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm) cover-to-cover. And if anyone has a good way to export highlights from a personal document in Kindle, please let me know as it's apparently unsupported.]

<em>
6.5.4.3 Java versus JavaScript
</em>

<em>
REST can also be used to gain insight into why some media types have had greater adoption within the Web architecture than others, even when the balance of developer opinion is not in their favor. The case of Java applets versus JavaScript is one example.
</em>

...

<em>The question is: why is JavaScript more successful on the Web than Java? It certainly isn't because of its technical quality as a language, since both its syntax and execution environment are considered poor when compared to Java. It also isn't because of marketing: Sun far outspent Netscape in that regard, and continues to do so. It isn't because of any intrinsic characteristics of the languages either, since Java has been more successful than JavaScript within all other programming areas (stand-alone applications, servlets, etc.). In order to better understand the reasons for this discrepancy, we need to evaluate Java in terms of its characteristics as a representation media type within REST.</em>

<em><b>JavaScript better fits the deployment model of Web technology. It has a much lower entry-barrier, both in terms of its overall complexity as a language and the amount of initial effort required by a novice programmer to put together their first piece of working code. JavaScript also has less impact on the visibility of interactions. Independent organizations can read, verify, and copy the JavaScript source code in the same way that they could copy HTML.</b> Java, in contrast, is downloaded as binary packaged archives -- the user is therefore left to trust the security restrictions within the Java execution environment. Likewise, Java has many more features that are considered questionable to allow within a secure environment, including the ability to send RMI requests back to the origin server. RMI does not support visibility for intermediaries.</em>

<em><b>Perhaps the most important distinction between the two, however, is that JavaScript causes less user-perceived latency. JavaScript is usually downloaded as part of the primary representation, whereas Java applets require a separate request. Java code, once converted to the byte code format, is much larger than typical JavaScript. Finally, whereas JavaScript can be executed while the rest of the HTML page is downloading, Java requires that the complete package of class files be downloaded and installed before the application can begin. Java, therefore, does not support incremental rendering.</b></em>

<a href='http://www.flickr.com/photos/psd/421186578/'>![Roy Fielding](http://i.imgur.com/NeHz2eI.jpg)</a>