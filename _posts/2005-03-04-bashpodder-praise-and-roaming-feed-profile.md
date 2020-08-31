---
id: 69
title: BashPodder Praise and Roaming Feed Profile
date: 2005-03-04T11:45:09+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=69
permalink: /bashpodder-praise-and-roaming-feed-profile/
dsq_thread_id:
  - "381848586"
  - "381848586"
categories:
  - SoftwareDev
---
As I've been doing some travelling, I've had to set up podcast clients on my laptop. Two issues:
* **It's a hassle to copy podcast client settings from one PC to another.** What I like about a service like [bloglines](http://bloglines.com) is that you're free to move between PCs. That's not so easy with Podcast clients which sit on your PC rather than a web server.
* **It's a hassle to install a new podcast client and add all the feeds.** I'd like to just have a list of feeds, and tick those I'm interested in. Instead, there's a 
whole lot of mousing involved for every single feed. That's using ipodder and BlogMatrix sparks, haven't set up .net framework to test the others.

So I decided instead to boot into linux and "set up"  [bashpodder](http://linc.homeunix.org:8080/scripts/bashpodder/). **Bashpodder config is so simple: just edit a single text file with all the feeds** and run it. **Bashpodder is a tiny podcast client written by [linc](http://linc.homeunix.org:8080), 44 lines of bash elegance.** There's still some issues with certain feeds and torrents, though the contributions on the bashpodder site apparently fix a lot of that.

Also, I wanted a way to permanently track my podcast feeds, so I can have something like the roaming profile that I have on bloglines. So the result was a little mod that wgets the config file from a webserver, and only looks at lines beginning with "http". I'll send it to [Linc](http://linc.homeunix.org:8080/) (Mr. BashPodder), but here are the main change if you want it.

The main changes were:

* Download the config file if a URL argument is specified
* Read only lines beginning with "#"
* Also "touch" podcast.log as I encountered an error running it first time (unmodified), if the log doesn't work.

Here's the full script after those few changes.

<pre>
</pre><pre><code>
#!/bin/bash
# By Linc 10/1/2004
# Find the latest script at http://linc.homeunix.org:8080/scripts/bashpodder
# Last revision 12/14/2004 - Many Contributers!
# If you use this and have made improvements or have comments
# drop me an email at linc dot fessenden at gmail dot com
# I'd appreciate it!
                                                                                
# Ensure podcast.log exists
touch podcast.log
                                                                                
# Grab fresh bp.conf from a URL if specified
if [ ! -z $1 ] ; then
  if [ -e bp.conf ] ; then
    mv bp.conf bp.conf.old
  fi
  wget -O bp.conf $1
fi
                                                                                
# Make script crontab friendly:
cd $(dirname $0)
                                                                                
# datadir is the directory you want podcasts saved to:
datadir=$(date +%Y-%m-%d)
                                                                                
# Check for and create datadir if necessary:
if test ! -d $datadir ; then
  mkdir $datadir
fi
                                                                                
# Delete any temp file:
rm -f temp.log
                                                                                
# Read the bp.conf file and wget any url not already in the podcast.log file:
while read feed ; do
  if [ ${feed:0:4} == 'http' ] ; then
    file=$(wget -q $feed -O - | tr 'r' 'n' | tr ' " | sed -n 's/.*url="([^"]*)".*/1/p')
    echo -e "---nFrom $feed, downloading:n$file"
    for url in $file ; do
      echo "Downloading $url"
      echo $url >> temp.log
      if ! grep "$url" podcast.log > /dev/null ; then
        wget --progress=dot -q -P $datadir "$url"
      fi
    done
  fi
done < bp.conf
# Move dynamically created log file to permanent log file:
cat podcast.log >> temp.log
sort temp.log | uniq > podcast.log
rm temp.log
# Create an m3u playlist:
ls $datadir | grep -v m3u > $datadir/podcast.m3u
</code></pre><!--da736bbf8abc5ea2751ced27656a5c34-->