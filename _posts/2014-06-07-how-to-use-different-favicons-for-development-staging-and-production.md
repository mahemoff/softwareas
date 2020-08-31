---
id: 1964
title: How to use different favicons for development, staging, and production
date: 2014-06-07T14:29:52+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1964
permalink: /how-to-use-different-favicons-for-development-staging-and-production/
categories:
  - SoftwareDev
tags:
  - Favicon
  - Rails
---
<a href='https://player.fm'>![](http://i.imgur.com/PsNjwvM.png)</a>

It's useful to have different favicons for each environment during development, as [Pamela recently pointed out](https://twitter.com/pamelafox/status/474922554012884992). Here's how I do it.

First, generate the images. Most graphics editor have some kind of Colorize tool and if you do it often, use ImageMagick to [change colors programmatically](http://www.imagemagick.org/Usage/photos/#chroma_key). If you're lucky enough to have a green brand logo, a cool combo would be traffic lights. Justsaying.

Now, set the favicons according to your environment. Should you just use /favicon.ico location or point to the location in head? The answer is both. /favicon.ico is useful for third-party plugins whose HTML you don't control, as well as quick hack pages you can't be bothered configuring with proper metadata. A link tag in html head is useful for revving the icon when it changes, to bust any cached version. So use both.

To set favicon in HEAD, ensure the path is dynamically generated instead of hard-coded:

[html]
%link(rel="icon" href="#{favicon_path}" type="image/x-icon")
[/html]

The path is generated like such as:

[ruby]
def env_suffix
  Rails.env.production? ? '' : "-#{Rails.env}"
end

def favicon_path
  asset_path "favicon#{env_suffix}.ico"
end
[/ruby]

It's arguably bad form to use "production" strings in production, so the env_suffix nonsense above will hide it. If you don't care about that, just call your production icon favicon-production.ico and save yourself a little hassle.

As mentioned earlier, we also want just /favicon.ico to exist. A quick way to do that is copy it when the apps starts or define /favicon.ico as a route and serve the file as favicon_path, defined above, with sufficient cache expiry time (e.g. 1 day). e.g.:

[ruby]
def favicon
path = ActionController::Base.helpers.asset_path "favicon#{env_suffix}.ico"
send_file path, type:"image/x-icon", disposition:"inline"
end
[/ruby]

For bonus points, you might want to use similar techniques to provide overriding stylesheets for development and staging. Then you can introduce a text label or change background color, etc.