---
id: 319
title: Roll on Rest On Ruby On Rails
date: 2006-06-28T07:24:55+00:00
author: admin
layout: post
guid: http://www.softwareas.com/roll-on-rest-on-ruby-on-rails
permalink: /roll-on-rest-on-ruby-on-rails/
dsq_thread_id:
  - "390301881"
categories:
  - SoftwareDev
tags:
  - Links
  - Rails
  - REST
  - SOAP
---
<img src="http://img70.imageshack.us/img70/2773/jigsawgreen060dy.png" align="right"/>

It's good to hear <a href="http://casperfabricius.com/blog/2006/06/25/railsconf-dhh/">Rails 1.2 is all about embracing REST</a>. Working with Ajax has helped me really appreciate <a href="http://ajaxpatterns.org/RESTful_Service">the benefits of REST</a>, and it all fits in with the Rails mindset quite nicely. Right now, we have URLs like

/user/update/5

whereas REST would have it as

/user/5

and then POST in the details - the nature of the method ("POST") tells you it's an update. Alternative we could send in a message with DELETE method if we wanted to delete user 5 instead. (In practice, there will be a slight hack to do this, involving a hidden field, because most browsers can only upload POST and GET).

<b>By piggybacking on the commonly accepted conventions of REST, there will be even more "convention over configuration" embodied in Rails.</b> And even greater division between RESTians and SOAPians. If nothing else, it's a smart way to attract people who get REST and repel those who push SOAP ;-). (Software Engineering Radio recently quipped SOA is now just a pure acronym (just like KFC, AOL, Ajax) ... it's not simple, object-oriented, or ?accessible.)<!--23380713c7202a4f86ce0ed5d827c0e0-->