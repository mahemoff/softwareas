---
id: 156
title: Prototyping Desktop Apps with Ajax?
date: 2005-07-05T23:50:40+00:00
author: admin
layout: post
guid: http://www.softwareas.com/prototyping-desktop-apps-with-ajax
permalink: /prototyping-desktop-apps-with-ajax/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "375572344"
  - "375572344"
categories:
  - HumansAndTech
  - Links
---
Tony Darugar on [prototyping with Ajax](http://www.parand.com/say/index.php/2005/07/05/ajax-as-prototyping-tool/):

> [A]s I went to download Tcl/Tk, it occured (sic.) to me that I could use AJAX. All Iâ€™m looking for is a simple screen that displays each record in turn. I can slap together the HTML page in no time. I can update the contents of the HTML page by simply slapping the values into javascript variables and evalâ€™ing the result on the browser. Nice and easy.

I'd generally advocate low-tech first and feature-driven design instead of software prototyping. But if you really need a quick and dirty prototype, is Ajax the way to go? If you were demonstrating a complex mathematical algorithm, for instance, **I think Ajax is a great way to make it interactive and *not* have to worry about installing it on the user's desktops.** One of the problems with software prototypes is the installation effort - evaluators need to upgrade upon each cycle, and at a time when installation scripts are usually not in place. That just slows down development - it means prototype reviews get put off and programmers are left wondering what to do next.

The post also highlights a general point about web applications: the zero-install is not just a benefit for end-users, but also speeds the development process, because no time is wasted installing and upgrading on the desktops of all the cameos. Before a serious system goes live, it's not uncommon - at least in large companies - for it to pass the eyeballs of client representatives, managers, testers, auditors, regulators, sysadmins, one or two generic politicians. If it's on the web, you can forget about most installation headaches.