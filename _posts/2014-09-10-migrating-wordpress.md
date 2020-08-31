---
id: 1990
title: Migrating WordPress
date: 2014-09-10T08:04:51+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1990
permalink: /migrating-wordpress/
categories:
  - SoftwareDev
---
After another WordPress migration [1], here's my 2p on WordPress migrations: Don't even think about following WordPress's standard backup-and-restore instructions. [The Duplicator plugin](https://wordpress.org/plugins/duplicator/) captures everything in one go, including comments, themes, etc as it dumps both the database and the file structure in a single archive. Also, you can easily scp the dump onto the new machine; whereas the usual procedure requires rebuilding WordPress, installing a plugin, and then worrying about the dump being too big when you try to upload it over HTTP (as there's still no obvious way to scp and restore WXR files, really!)

Duplicator's restore phase isn't too clear from the docs, but [I found the answer here](http://lifeinthegrid.com/support/knowledgebase.php?article=3). You don't have to manually install WordPress. You simply create a new temp folder somewhere under web servers public/ folder, open your browser, and navigate to the install.php file there in this folder. It will do the rest for you!

1. Now that Linode has dropped its minimum box to [$10/month](https://www.linode.com/pricing) (and a decent spec at 1GB RAM with SSD storage), I decided to consolidate and move the utility box on Linode instead of DigitalOcean.