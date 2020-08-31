---
id: 1473
title: 'The Weirdness of Ajax Redirects: Some Workarounds'
date: 2011-12-12T18:16:40+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1473
permalink: /the-weirdness-of-ajax-redirects-some-workarounds/
dsq_thread_id:
  - "502189407"
categories:
  - SoftwareDev
tags:
  - Ajax
  - HTML History
  - HTTP
  - Rails
  - REST
  - XMLHttpRequest
---
I've been dealing with the situation when your server redirects after a DELETE. Which is actually a fairly common use case. User deletes a blog post, redirect them to the index of all posts. The article below has some Rails workarounds, but is relevant to anyone using XHR and perhaps HTML5 History, ie many single-page web apps.

It's important stuff to know if you're HTML5ing in earnest, because there was a recent change to Chrome which makes it standard-compliant, but fundamentally different to other browsers and also makes it handle DELETE and other verbs different to how it handles POST and GET.

<h3>DELETE redirection</h3>

This redirection becomes troublesome if you want to do this in a way which will seamlessly support Ajax calls, as well as standard web requests. It's troublesome because of a lethal combination of two browser facts.

Firstly, XHR automatically follows redirects. Your JavaScript has no way to jump in and veto or alter any redirect that comes from the server. XHR call fires off to server, server responds with 302 status code and a location header, the browser *automatically* issues a new request to the specified location.

Secondly, a DELETE request, when it's redirected, will actually cause another DELETE request to the new location. Yes, if you're redirecting to the index, congratulations ... your server now receives a request to DELETE the fraking index. You lose!!! So the very normal thing to do for a non-Ajax app suddenly becomes an epic tragedy. It's completely unintuitive, but it's actually the standard! I learned as much by filing <a href='http://code.google.com/p/chromium/issues/detail?id=107159'>an erroneous Chrome bug</a>. Turns out Chrome's unintuitive behaviour is actually correct and Firefox and Opera were wrong. Even more confusing, I was seeing POST requests being converted to GETs, and it turns out this is also part of the 302 standard - POSTs can be converted to GETs, but not DELETEs (or PUTs etc I assume).

Just now, I made a little workaround which seems to be working nicely in my case. In my AppController, which is my app's own subclass of ActionController, I simply convert any 302 response (the default) to a 303, for redirect_to calls. I should maybe do this for XHR calls only, to be "pure" when a normal call comes in, but no real difference anyway.

[ruby]
class ApplicationController < ActionController::Base

  ...

  # see src at https://github.com/rails/rails/blob/master/actionpack/lib/action_controller/metal/redirecting.rb
  def redirect_to(options = {}, response_status = {})
    super(options, response_status)
    self.status = 303 if self.status == 302
  end

end
[/ruby]

<h3>Finding the new location</h3>

While I'm blogging this, let me tell you about another related thing that happens with redirects (this section applies to any type of request - GET, POST, DELETE, whatever). As I said above, XHR will automatically follow requests. The problem is, how do you know where the  ultimate response actually came from? XHR will only tell you where the initial request went; it refuses to reveal what it did afterwards. It won't even tell you *if* there was any redirect. Knowing the ultimate location is important for HTML5 apps using the History API, because you may want to pushState() to that location. The solution is to have the web service output its own location in a header. Weird that you have to, but gets the job done.

[ruby]
class ApplicationController < ActionController::Base
  ...
  before_filter proc { |controller| controller.response.headers['x-url'] = controller.request.fullpath }

end
[/ruby]