---
id: 363
title: 'Tables &#8211; The Secret Behind Every Simple CSS Form'
date: 2007-02-12T04:47:01+00:00
author: admin
layout: post
guid: http://www.softwareas.com/tables-the-secret-behind-every-simple-css-form
permalink: /tables-the-secret-behind-every-simple-css-form/
dsq_thread_id:
  - "375169188"
categories:
  - SoftwareDev
tags:
  - CSS
  - HTML
  - Tables
  - Web
---
Tableless forms are painful. Every time I start trying to create them, I wonder why I am going through the motions. Some vague sense that it will be "more accessible" and I'll be able to tick an abstraction of a "web standards-compliant" box. But really, these table-less constructs are supposed to make page authoring easier, not harder. In the case of forms, table-less CSS makes it much harder.

Here are some examples of popular blog articles explaining how to create table:

<a href="http://jeffhowden.com/code/css/forms/">CSS-Only, Table-less Forms (Jeff Howden)</a> "Most of the CSS-only, table-less forms available suck." He's talking from an aesthetic perspective, not programming perspective whose suckiness I speak of here. What he does though, is show how to make a pretty form. The rub is over 300 lines of standard-formatted CSS, let alone the HTML. He does a good job, and I have no reason to question that the 300 lines is required; it's a sad reflection of what's required to make a neat form, albeit a fairly complex one.

<a href="http://alistapart.com/articles/prettyaccessibleforms">A List Apart on Accessible Forms</a> A more pedestrian tutorial on the basics of table-less forms. Weighing in at a mere 46 lines of CSS.

Using a table and just a handful of CSS lines, you can achieve pretty similar stuff. It won't get an accessibility auditor's magic tick, even though it will probably be quite accessible. It won't be a semantically valid structure either. That won't actually bother your users or any modern search engine, but if the thought scares you, you should get started with those floats and clears. For all these problems, you'll be rewarded with one great benefit: you'll be able to build it in a matter of minutes.

For typical forms where you want to be agile and get the thing published, stick with tables.