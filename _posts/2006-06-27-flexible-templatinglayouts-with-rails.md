---
id: 317
title: Flexible Templating/Layouts With Rails
date: 2006-06-27T09:59:01+00:00
author: admin
layout: post
guid: http://www.softwareas.com/flexible-templatinglayouts-with-rails
permalink: /flexible-templatinglayouts-with-rails/
dsq_thread_id:
  - "375573004"
categories:
  - SoftwareDev
tags:
  - Layout
  - Rails
  - RHTML
  - Ruby On Rails
---
Rails' layout mechanism follows the standard pattern embodied in <a href="http://java.sun.com/blueprints/patterns/">Sun's J2EE patterns</a> and familiar to users of Struts and other frameworks. The page template outputs the main content, and it's automatically wrapped by a generic template (as opposed to the earlier SSI-style paradigm, where each page manually includes headers, footers, etc.). <b>There's always a complication with this pattern, which is that the page author usually wants to influence some aspects of the wrapping as well.</b>

For instance, you're writing books.rhtml for an E-Commerce site. You're obviously going to set the main content - a list of books - but you also want to influence the wrapping, such as: change the page title (in the doc head), highlight "books" in the side menu, etc.

With many frameworks, you have to jump in to an XML file to influence the wrapping, which often means no-one bothers, and usability - not to mention search engine optimisation - suffers as a result...all pages end up with the same title and meta-information, and you're probably downloading extra Javascript because you've made it the same for all pages.

Rails makes it quite easy, and being Rails, there's no funny config files to mess with...it's all code. <b>The layout template is parsed <i>after</i> the main content, so the main content can set any variables, and the layout template can make use of them.</b>

For example, standard-layout.rhtml says:
[html]
<html>

<head>
    <title><%= @page_title || "My App" %></title>
</head>
[/html]

Then, <b>each page gets to choose its own title</b>, e.g. books.rhtml:
[html]
<% @page_title="Book Bargains" %>

<!-- Main content for books -->
<h1>Lots of Books Today!</h1>
....
[/html]

It's easy to make Javascript (and CSS) flexible. The main layout loops through each specified script:

[html]
<% (@scripts||[]).each do | script | %>
    <script type="text/javascript" src="/javascripts/<%= script %>.js"></script>
<% end %>
[/html]

(Some people might prefer Rails' script_include tag instead of manual <tt>script</tt> tags.)

Then, the page can optionally indicate the Javascripts it needs
[html]
<% @page_title="Book Bargains" %>
<% @scripts = ["dojo", "util", "books"] %>

<!-- Main content -->
[/html]