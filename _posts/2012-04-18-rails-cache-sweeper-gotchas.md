---
id: 1646
title: Rails Cache Sweeper Gotchas
date: 2012-04-18T02:53:43+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1646
permalink: /rails-cache-sweeper-gotchas/
categories:
  - SoftwareDev
tags:
  - Cache
  - Rails
  - Sweeper
---
As you'll [see here](http://stackoverflow.com/questions/1463714/in-rails-a-sweeper-isnt-getting-called-in-a-model-only-setup), Rails cache sweepers are a tricky subject. Here are some general things I've learned.

* [Sweepers are dual creatures](http://codelevy.com/2008/03/04/rails-caching-sweepers-controllers-and-models). "Here’s the scoop: sweepers observe both your models and your controllers. They’re not half-this and half-that, they’re both_. You can define model callbacks (after_save, afterupdate, etc.), and you can also define before/after callbacks for any controller action (e.g. after_list_create)."

* Notwithstanding the above, most references and despairing workarounds focus on their _controller_ nature. Dandy for a web forms app, but in my case, cached content is being invalidated by daemon processes operating directly on models.

* There's no standard home for Sweepers. So much for convention-over-configuration :). So I opted for a new app/sweepers directory and added it in `application.rb`: `config.autoload_paths += %W(#{config.root}/app/sweepers)`.

* Now to the crux of the matter: The Sweeper still does nothing, even if it's in the path. I don't know why, but it's a common problem! I had to explicitly add it as an observer: `config.active_record.observers = :episode_sweeper`. This is the _model_ equivalent of people explicitly adding it to their _controller_ with an `after_update` hook.

* Now to the crux of the matter, redux: Okay, so now the sweeper is being called when models change (specifically, the models it declares it's observing). Great. But it still doesn't work &mdash; `expire_fragment` apparently doesn't, because I'm still seeing the the old fragment appear in the web app. **WAT?** The answer turned out to be, don't just call `expire_fragment()`. Instead, call `ActionController::Base.new.expire_fragment()`. It seems the fragment used when outputting a view is not the same as that expired by `expire_fragment()`. I'm only telling you what worked here, I can't tell you why!

* You can also expire cache in the Rails console for testing purposes, just call `ActionController::Base.new.expire_fragment()`. (I think you need to restart Rails (and the console) if you update the sweeper code, given that it's set up as an arel observer in the config line above. But haven't fully tested that.)

This is just a basic implementation for now. A better implementation is probably to use DHH's [key-based caching approach](http://37signals.com/svn/posts/3113-how-key-based-cache-expiration-works), which has the neat principle of generating a new key every time the fragment changes.

<script src="https://gist.github.com/2410695.js?file=episode_sweeper.rb"></script>