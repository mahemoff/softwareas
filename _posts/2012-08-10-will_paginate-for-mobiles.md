---
id: 1804
title: will_paginate for mobiles
date: 2012-08-10T13:05:59+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1804
permalink: /will_paginate-for-mobiles/
categories:
  - SoftwareDev
---
I've been using ElasticSearch + Tire to (finally!) build Player FM search and they've worked well.

One little trick I used just now is a responsive pagination. I'm using will_paginate and bootstrap_will_paginate gems for this.

Normally, you get this clutter on mobile:

<div style='border: 1px solid #600;'>
<img src='http://i.imgur.com/Z5G01.png' />
</div>
<i>messed up!</i>

Fortunately, will_paginate marks classes semantically, so you can do this instead:

<div style='border: 1px solid #060;'>
<img src='http://i.imgur.com/BQPBS.png' />
</div>
<i>responsive joy</i>

using a SASS media query:

[css]
.pagination
  @media (max-width: 480px)
    li   
      display: none
      &.active,&.prev,&.next
        display: inline
[/css]

I think there are some other ways to do it via server-side mobile detection, but this was a simple and reliable trick.