---
id: 2096
title: 'Speeding up Rails asset loading in development: Tips and Gotchas'
date: 2015-04-08T15:59:13+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2096
permalink: /speeding-up-rails-asset-loading-in-development-tips-and-gotchas/
categories:
  - Uncategorized
---
Rails can be so productive, but one big exception is asset serving in development. Loading HTML, scripts, stylesheets, images, fonts, etc can be slow, sometimes 10+ seconds per page if things go wrong.

Here are some tricks and gotchas to help improve asset speed in development. I've learned each of them the hard way, after messing around with settings in a rush to get things working.

### Ensure caching is on

[ruby]
\# config/environments/development.rb:
config.action_controller.perform_caching = true
[/ruby]

Assets may compile slowly, but at least make them compile slowly only once, not every time. To ensure assets are cached, make sure caching is on.

### Ensure the configured cache is working/running

Continuing the previous point, make sure caching is working. I normally use memcached via dalli gem, so I have a config line like this:

[ruby]
\# config/application.rb:
config.cache_store = :dalli_store, 11211, { namespace: 'player', pool_size: 10 }
[/ruby]

The important thing is to make sure memcached is running. I've left it off at times to guarantee cache is busted on each request, forgetting it's off when I see slow page loads.

If you're using the default file cache, make sure it's writeable by the Rails process and there's free disk space. Check files are being created.

### Ensure browser caching is on

In a tool like Chrome devtools, it's easy to flip HTTP caching on and off. With HTTP caching on - the default for browsers and their normal users - requests will include if-changed-since and last-modified. As with regular requests, Rails assets will serve faster if those things are turned on and that's a good simulation of the production environment too. However, you will sometimes need to turn caching off to test changes; just be aware that this one can substantially speed up assets serving and developers probably turn it off too readily.

### Turn debug off

[ruby]
\# config/environments/development.rb:
config.assets.debug = false
[/ruby]

This one's another trade-off. It will munge your assets together, which usually means faster load times. e.g. if you have an application.js with `//= require book` and `//= require author`, you'll end up with a single file with both. I've not been able to get Coffee/Sass mappings working under those conditions, so it makes debugging harder.

### Inject styles and scripts dynamically

Web pages can easily update stylesheets and scripts just by adding a style or script tag. This is super-helpful during development because it means you don't have to serve a whole new page from the server if you are just messing with styles or scripts. I use a keyboard shortcut to automatically refresh the stylesheet with a cache-busted update. (It could also be more fine-grained if debug is turned off).

[javascript]
Mousetrap.bind 's', U.reloadStylesheets
 U.reloadStylesheets = ->
   showDialog 'Loading stylesheet'
   $('link[href^="/assets/application.css?body=1"]').remove()
   $("<link rel='stylesheet' type='text/css' href='/assets/application.css?body=1&#{Math.floor(1e6*Math.ran
 dom())}' />").appendTo('body')
[/javascript]

There's a more sophisticated, more automated, approach to [injection here](https://mattbrictson.com/lightning-fast-sass-reloading-in-rails).

### Libsass

[Libsass](https://github.com/sass/libsass) is a fast rewrite of Sass in C. This makes every programmer happy except for Rubyists, who may feel bittersweet about Ruby Sass being obsoleted. But still, it's happening and there is indeed [a Ruby binding for it](https://github.com/sass/ruby-libsass) which should be much faster than the pure Ruby Sass. I'm talking [10x faster](http://www.solitr.com/blog/2014/01/css-preprocessor-benchmark/), potentially.

The main downside right now is compatibility. Not all features have been ported and not all of Compass will work presently, is my understanding, though I've also seen a [report](https://twitter.com/kaelig/status/390478769607413761) that Bourbon *is* now fully compatible, so that's exciting progress. I do think the benefits will be too great and eventually Libsass will be The One for all things Sass.

So the advice here is to consider compiling with Libsass instead of Sass. Easier if you are starting a new project from scratch. I haven't done this myself, though I noticed a while back Guardian did.

### Avoid external dependencies

If you have scripts such as analyics or widgets, take steps to either not load them during development or defer loading so they don't block anything. (Good advice for production anyway.) The last thing you want is a slow Twitter widget stopping your assets from even beginning to compile.

### Consider parallel loading

Using a server like unicorn, you can configure parallel processing. This is another big trade-off. You'll have trouble debugging and reading log files (though you can also separate log files per process).

### Consider precompilation

You can, in some cases, precompile like you would in production. This is useful if you are writing and testing only back-end updates. However, a lot of the time, you should hopefully be writing tests for those and not actually testing in the browser much; in which case precompilation won't be so useful after all.

### Understand the fundamental asset model

[Read this](http://stackoverflow.com/a/8827757/18706) and [this](http://guides.rubyonrails.org/asset_pipeline.html) to really understand what's going on. There's a lot of quick fixes around (such as those herein) but it can all seem like magic and still leave problems if you're not following it.