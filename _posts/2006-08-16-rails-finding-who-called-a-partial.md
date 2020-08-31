---
id: 340
title: 'Rails: Finding Who Called A Partial'
date: 2006-08-16T09:20:41+00:00
author: admin
layout: post
guid: http://www.softwareas.com/rails-finding-who-called-a-partial
permalink: /rails-finding-who-called-a-partial/
dsq_thread_id:
  - "375573078"
categories:
  - SoftwareDev
tags:
  - ERb
  - Partials
  - Rails
  - Ruby
  - Web
---
So you're coding a partial and you want to know which template has pulled it in. The magic word is <b>"@first_render"</b>, which will give you something like "homepage/admin" for the homepage/admin.rhtml template. Trivial, I know, but I couldn't find any mention of it after much googling, so I decided to output self.inspect and was pleased to find that property. I have no idea how reliable it is, if it will survive to Rails 1.2 and beyond, etc, etc, caveat, disclaimer, etc. I do think developers could benefit if Rails explicitly supported the property ... just like knowing who called a function, there are always good reasons to do it, and the Ruby philosophy is to give developers the power to choose what's good for them.

I'm using the property in a tabbed navigation partial, to determine which is the current page. A classic example of where the temlpate property is useful, since the property is used in a generic way, not as part of some complex "if" loop (viz "if template is leftColumn, make the background pink" etc.)

[ruby]
css_classes = ["templateA", "templateB", "templateC"].map {
  |template| @first_render==template ? "on" : "off"
}
[/ruby]
	
[html]
<div class="nav">
  <a class="<%= css_classes[0] %>" href="/controllerX/actionA">The A Thang</a>
  <a class="<%= css_classes[1] %>" href="/controllerX/actionB">The B Thang</a>
  <a class="<%= css_classes[2] %>" href="/controllerX/actionC">The C Thang</a>
</div>		
[/html]

(It could be refactored to use some tag helpers and an associative array mapping actions to css classes.)<!--9ac3b2332a19ca1e121c10205480ae36-->