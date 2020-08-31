---
id: 499
title: 'BashPodder mod &#8211; add podcasts to iTunes'
date: 2008-12-04T02:09:50+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=496
permalink: /bashpodder-mod-add-podcasts-to-itunes/
dsq_thread_id:
  - "375574015"
categories:
  - SoftwareDev
tags:
  - Bash
  - bashpodder
  - itunes
  - Podcasting
  - shell
  - Unix
---
<a href="http://www.gizmodo.com.au/2008/04/review_lasonic_i931_ipod_ghetto_blaster_verdict_awesome-2.html"><img src="http://picupper.com/2008/12/03/lasonici9312_medium.jpg" style="width:380px;"></a>

As a podcatcher (<a href="http://softwareas.com/seven-things-about-itunes-that-are-just-plain-wrong">among other things</a>), iTunes sucks. Badly. <a href="http://juicereceiver.sourceforge.net/ ">iPodder</a> is nicer, mainly because I can keep my follow list in the cloud at <a href="http://www.podnova.com/">PodNova</a>. However, it (or the combination with podnova) often ends up downloading gigs of old stuff, on some particular feeds. Worse, it consumes obscene quantities of memory and CPU, with its UI being unresponsive to the point of being unusable, like 30 second or more delays for each gesture. This is on an early macbook.

Anyway, I decided to rectify the situation and go back to bashpodder, a tiny shell script which proves the point that a podcatcher need not be grandiose, nor a resource gobbler. It's also cool as it's easily customisable for anyone with some bash-fu. <a href="http://softwareas.com/bashpodder-praise-and-roaming-feed-profile">I modded it a few years back</a> to keep my follow list in the cloud. (I believe clouds were called "servers" back then.)

I've recently modded bashpodder to add files to iTunes. Yes, I still like iTunes and I definitely like the i* players which are, for most intents and purposes, constrained to the universe of iTunes. As for it's podcatcher, not cool. The interface for exploring podcasts is cumbersome, and the result, the downloaded podcasts, are not handle with care. For example, if you download podcasts with iTunes, it marks them out specially as podcasts, and there's no way to, say, delete all podcasts older than a week. If they're normal tracks added from an external catcher, they're just regular MP3s and you can do what you like with them. And you can't keep your follow list in the cloud!

So here's bashpodder modified to add to itunes. (The itunes part I added is the HERE doc section beginning with /usr/bin/osascript. You could easily extend it to, say, tag podcasts from certain feeds with a certain album name.)

Click on "Plain Text" and cut-and-paste it into a shell file. Easiest would be to download the several files required for <a  href="http://www.lincgeek.org/bashpodder/">bashpodder</a> (there should be a mod to make it just a single self-modifying file), and replace bashpodder.shell contents with that below.

[javascript]
#!/bin/bash
# By Linc 10/1/2004
# Find the latest script at http://linc.homeunix.org:8080/scripts/bashpodder
# Revision 1.2 09/14/2006 - Many Contributers!
# If you use this and have made improvements or have comments
# drop me an email at linc dot fessenden at gmail dot com
# I'd appreciate it!

# Make script crontab friendly:
cd $(dirname $0)

# datadir is the directory you want podcasts saved to:
datadir=$(date +%Y-%m-%d)

# create datadir if necessary:
mkdir -p $datadir

# Delete any temp file:
rm -f temp.log

# Read the bp.conf file and wget any url not already in the podcast.log file:
while read feed
  do
  podcast=`echo $feed | cut -f 1 -d ' '`
  echo $podcast
  file=$(xsltproc parse_enclosure.xsl $podcast 2> /dev/null || wget -q $podcast -O - | tr 'r' 'n' | tr ' " | sed -n 's/.*url="([^"]*)".*/1/p')
  for url in $file ; do
    echo "Retrieving $url"
    echo $url >> temp.log
    if ! grep "$url" podcast.log > /dev/null
      then
      # wget -t 10 -U BashPodder -c -q -O $datadir/$(echo "$url" | awk -F'/' {'print $NF'} | awk -F'=' {'print $NF'} | awk -F'?' {'print $1'}) "$url"
      outpath=$datadir/$(echo "$url" | awk -F'/' {'print $NF'} | awk -F'=' {'print $NF'} | awk -F'?' {'print $1'})
      curl --retry 10 -C - $url > $outpath
      fullpath=`pwd`/"$outpath"
      /usr/bin/osascript <<-EOF
        tell application "iTunes"
          set posix_path to "$fullpath"
          set mac_path to posix_path as POSIX file
          set new_track to add mac_path
          set genre of new_track to "*Podcast"
        end tell
EOF
    fi
    done
  done < bp.conf
# Move dynamically created log file to permanent log file:
cat podcast.log >> temp.log 
sort temp.log | uniq > podcast.log
rm temp.log
# Create an m3u playlist:
ls $datadir | grep -v m3u > $datadir/podcast.m3u
[/javascript]

<a href="http://www.lincgeek.org/bashpodder/"><img style="width: 280px;" src="http://picupper.com/2008/12/03/bashpodder.png"></a>