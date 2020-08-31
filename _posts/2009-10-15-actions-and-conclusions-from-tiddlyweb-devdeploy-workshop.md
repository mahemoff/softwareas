---
id: 676
title: Actions and Conclusions from TiddlyWeb Dev/Deploy Workshop
date: 2009-10-15T17:07:35+00:00
author: admin
layout: post
guid: http://softwareas.com/actions-and-conclusions-from-tiddlyweb-devdeploy-workshop
permalink: /actions-and-conclusions-from-tiddlyweb-devdeploy-workshop/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "375574488"
categories:
  - SoftwareDev
---
<h3>Background</h3>

As everyone's been developing in different ways, I wanted to arrange a
session to share experiences and come up with best practices - to help
us become (a) more consistent and (b) more productive going forward.

We agreed on objectives (20min), explained our current practices
(1hr), had a general discussion and debate on deployment and
development (1hr), and we then performed an interesting activity
@cdent had suggested earlier on, which was to do a group coding
session in front of a projector. You could think of it as an enhanced
meeting more than "pair programming on steroids". Part of it was for
Chris to explain the tiddlyweb tools that we should be using more, and
part of it was to walk through a project lifecycle and critique the
stages. This was 2 hours, we concluded the event, and Chris, Fred
(@FND), and I remained to refine some of the points into the following
summary.

<h3>Best Practices and Required Tooling</h3>

Best Practices we agreed on:

- Deployment - Release verticals as SetupTools modules
[tarball is for people who want to play with the source
egg is for people who just want to install it
If you distribute the tarball, you're effectively distributing the
egg; you can build it from the tarball]

- Deployment - Release mature plugins as SetupTools modules
This way, verticals can refer to them as depencies for auto-update
("assemble and aggregate" as @FND put it); in the event of verticals
using "immature" plugins (just ".py" files form the web), they can
include it in their own package

- Dev - develop in the dev store, which will be re-created/upgraded
We'll be discussing features for the new/upgraded dev store on irc tomorrow.
It will need to offer a way to include files anywhere on the hard
drive, and also in remote locations (http; ideally svn, git, etc)

- Dev/Deploy - use bash scripts
 * "tiddlyspawn" (name TBA) creates a new project (probably using
twinstance, the 2009 AD reincarnation to "twanager instance", among
other things);, inheriting config from tiddlywebwiki.config, make src
dir, "parse" setup.py to find dependencies and run "easy_install" on
them, perhaps make static dir
 * "build.sh" - inside the project to run updates, pull in remote
plugins, build setuptools tarballs for release

- Project dir structure (indicative)
<pre>
/setup.py  # python setuptools recipe - stub's created by build.sh
/build.sh # the all-singing build.sh
/component.yml #
/instance
/src
/static
/dist
</pre>

<a href="http://www.flickr.com/photos/psd/4013410477/" title="TiddlyWeb Pow-Wow (by psd)"><img src="http://farm4.static.flickr.com/3515/4013410477_68b47f8735.jpg" title="TiddlyWeb Pow-Wow (by psd)" alt="TiddlyWeb Pow-Wow (by psd)" width="400" height="302" /></a>

<a href="http://www.flickr.com/photos/psd/4014368262/" title="Osmosoft Collectively Exploring TiddlyWeb (by psd)"><img src="http://farm4.static.flickr.com/3484/4014368262_422ed7e6bc.jpg" title="Osmosoft Collectively Exploring TiddlyWeb (by psd)" alt="Osmosoft Collectively Exploring TiddlyWeb (by psd)" width="400" height="274" /></a>