---
id: 384
title: 'Ruby/Rails: Overriding NilClass'
date: 2007-06-25T20:32:26+00:00
author: admin
layout: post
guid: http://www.softwareas.com/rubyrails-overriding-nilclass
permalink: /rubyrails-overriding-nilclass/
dsq_thread_id:
  - "375196627"
categories:
  - SoftwareDev
tags:
  - NilClass
  - Rails
  - Ruby
---
Rails uses "whiny nil", which means if you call a method on an object that happens to be nil (null), you get an exception. This is good. But with strings in a web app (in any language), you often don't know if an empty string will be nil or simply zero-length (""). That's because some code will see a form submitted with a whitespace string and make it nil, while others will make it "". These might be my libraries or the web framework's libraries or plugin libraries. This leads to ugly code like this:

[ruby]
@message = "Oi! Enter your name fella" if name or name.empty?
[/ruby]

When we really just want
[ruby]
@message = "Oi! Enter your name fella" if name.empty?
[/ruby]

So I derive great pleasure from overriding NilClass like so:
[ruby]
class NiClass
  def empty?
    true
  end
end
[/ruby]