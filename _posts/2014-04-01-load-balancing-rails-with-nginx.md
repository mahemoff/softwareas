---
id: 1944
title: Load-balancing Rails with Nginx
date: 2014-04-01T11:05:30+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1944
permalink: /load-balancing-rails-with-nginx/
categories:
  - SoftwareDev
tags:
  - devops
  - nginx
  - Rails
---
<img src='http://i.imgur.com/6f56UZ9.jpg' />

Well this was some fine undocumented black magic. I've got [Player FM](https://player.fm) behind a load balancer now, using the following Nginx config. I'll explain some more about the overall upgrade later.

    # App load balancer

    upstream playerhost {
     server 192.168.1.1;
     server 192.168.1.2;
    }

    server {

      server_name playerhost;

      location / {

        proxy_set_header Authorization "Basic blahblahblah==";
        proxy_next_upstream http_500 http_502 http_503 http_504 timeout error;

        # http://stackoverflow.com/questions/16159998/omniauth-nginx-unicorn-callback-to-wrong-host-url
        proxy_set_header Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Client-IP $remote_addr;
        proxy_set_header X-Forwarded-For $remote_addr;

        proxy_redirect http://playerhost http://player.fm;
        proxy_redirect https://playerhost https://player.fm;
        proxy_pass http://playerhost;

      }
    }

### Notes

* I recommend using a distinct name for the backend (I've used "playerhost"). Most tutorials use the non-descript "backend", but it's a useful indicator if something's going wrong as you'll see this ID pop up in URLs and HTML content.
* You don't have to use basic auth for the backends. You could just firewall them off the public internet or deal with them being public. Being public is not clean and will cause the site to be hit by search bots and so on unnecessarily. But closing it off altogether is not ideal, because it's useful for diagnostics to go into the backend servers. So I expose them via basic auth. The "blahblahblah" is base64 of your basic auth username:password.
* The site mostly worked without set_header, but I had some weird oAuth redirect problems and occasional HTML problems. In both cases, I'd be seeing that "playerhost" URL instead of the actual domain. This fixed it.
* The proxy_redirect commands were an earlier attempt to fix https redirections, and worked, but still left the problem mentioned in the previous point. It may not be necessary at all, after adding the set_headers. I haven't tested that yet.

Photo Credit: <a href="http://www.flickr.com/photos/35785593@N07/5716847705/">Graham Cook</a> via <a href="http://compfight.com">Compfight</a> <a href="https://creativecommons.org/licenses/by-nc-nd/2.0/">cc</a>
