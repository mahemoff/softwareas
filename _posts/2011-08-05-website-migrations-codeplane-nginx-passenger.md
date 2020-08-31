---
id: 1275
title: 'Website Migrations: CodePlane, Nginx, Passenger'
date: 2011-08-05T19:52:56+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1275
permalink: /website-migrations-codeplane-nginx-passenger/
dsq_thread_id:
  - "380724998"
categories:
  - General
  - SoftwareDev
tags:
  - Hosting
  - Linode
  - Navel-Gazing
  - Passenger
  - PHP
  - Ruby
  - SliceHost
---
I'm just about done (famous last words) with a long, and not just a bit tedious, migration from Slicehost to Linode. Both are "cloud-style" VPSs, where you can do immediate one-click backups, cloning, upgrading, etc. As VPSs, you get to choose a raw initial Linux stack, and you're then on your own to add on web servers, command-line tools, etc.

While SliceHost has worked out fine, notwithstanding [the 2008 exit of its founders]((http://37signals.com/founderstories/slicehost), Linode has much better rates these days and also seems to be gaining traction with the NodeJS community. Maybe it's the fortunate name affinity. There's also [the distinct possibility](http://thenextweb.com/dd/2011/05/03/rackspace-to-shut-down-slicehost/) Slicehost's parent Rackspace will close down Slicehost itself and move things over to Rackspace. They also have great support docs. In any event, I've really been wanting to migrate from lighty to nginx and start using CodePlane for code repo, so I was going to be stuck doing some work anyway.

A few random notes ...

### Setup

I don't intend this to be a review of Linode. Suffice to say, it was a super-easy process, and the [Getting Started guide](http://library.linode.com/getting-started) made everything nice and simple. Anyone coming from a similar environment like Slicehost would have no trouble. A nice bonus is the built-in monitoring charts, basically the kind of thing you'd get from a monit install, but right there on the admin panel, with no need to install anything. They're powered by [RRD](http://www.mrtg.org/rrdtool/).

Another nice bonus is ipv6 support. It's been a long time coming, but I'm finally ready for the internet of IP-labelled things and beyond! 173.255.208.243? That's not cool. You know what's cool? 2600:3c01::f03c:91ff:fe93:5a3e/64.

![](http://picupper.com/2011/08/05/billions-vpo.jpg)

### Passenger on Nginx

I'd previously used Thin on Nginx, but Passenger promised to be a lot easier. Turned out maybe not, <a href="http://www.modrails.com/install.html">Passenger</a> needs a custom Nginx install. I'd already set up Nginx with apt-get, and in retrospect, I should have tried to roll it back. So there was some challenges configuring things (the default Passenger-powered nginx goes into /opt/nginx, whereas the Ubuntu one is customised for the usual suspects on ubuntu, binary in /usr/sbin, conf in /etc/, and so on).

With the custom <a href="http://library.linode.com/frameworks/ruby-on-rails-nginx">Passenger-powered Nginx</a>, the core Nginx config needs no passenger or ruby reference. (ie You don't do the apache/lighttpd equivalent of declaring a dynamic modules - the lack of such things is why the custom nginx install is necessary). You only need to declare passenger in the site-specific config. For a Sinatra app, with config.ru at /path/to, you do this:

<pre>server {
  passenger_enabled on;
</pre>
<pre>
  location /static {
  root /path/to/public;
  index index.html index.html;
}</pre>

(Yes, you never need to point directly to the config.ru or its directory.)

### PHTML Suffix

I still have some weird bug preventing *.phtml files running. If no-one <a href="http://stackoverflow.com/questions/6955086/nginxfcgi-phtml-suffix-not-running-php">knows the answer</a>, I'll just rename it.

### Mediawiki

After much messing around, I ended up with something that works for the (unendorsed, I think) "cool URI" scheme, i.e. site.com/EntryName. (versus  site.com/index.php?title=EntryName).

<pre>
  location / {
    rewrite ^/([a-zA-Z0-9_:]+)$ /wiki/index.php?title=$1 last;
    rewrite ^/$ /wiki/index.php?title=Main_Page last;
    root  /path/to/public;
  }
</pre>

Self-explanatory I think. Along the way, I learned about nginx's "try_files" mechanism, which fits nicely with many PHP CMSs like WordPress and Mediawiki, where a single front controller is the gateway to the entire app. You can do stuff like  <a href="http://michaelshadle.com/2010/08/20/front-controller-patterns-and-nginx">try_files $uri $uri/ /index.php?page=$request_uri</a>...though I didn't need it here.

### WordPress

wordPress was similarly simple:

<pre>
    if (!-e $request_filename) {
      rewrite ^/(.+)$ /index.php?p=$1 last;
    }
</pre>

One quirk I discovered was I couldn't do online changes using the SFTP facility. This happened at Slicehost too. I eventually [discovered the cause](http://wordpress.org/support/topic/wp-27-error-failed-to-connect-to-ftp-server-http#post-994292). The directory needs to be owned by the webserver. The confusing thing is it looks like SFTP isn't set up right or you have the password wrong or something. Glad to know this.

### CodePlane

On a slightly separate note, I started using <a href="http://codeplane.com">CodePlane</a> as a code repo. It's similar to GitHub's private repo, but allows for unlimited projects. While I'd want to support GitHub, given all the value it provides, it's not feasible to store dozens of small throwaway projects there, so CodePlane is really neat so far. And the developer is highly responsive. I noted on GetSatisfaction that the homepage doesn't personalise if you're logged in, he fixed it in a matter of hours. He's also been open to engaging about some other suggestions I had. So it's working out nicely so far.