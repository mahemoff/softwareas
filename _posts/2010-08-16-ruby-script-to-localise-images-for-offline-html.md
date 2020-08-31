---
id: 953
title: Ruby Script to Localise Images for Offline HTML
date: 2010-08-16T00:18:36+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=953
permalink: /ruby-script-to-localise-images-for-offline-html/
dsq_thread_id:
  - "377008234"
categories:
  - SoftwareDev
tags:
  - offline
  - Ruby
---
I'm maintaining a custom HTML5 slide framework. A little similar to the canonical <a href="http://slides.html5rocks.com/">slides.html5rocks.com</a> insofar as, well, it's HTML5 and slides horizontally! But the key difference is that it's very markup-based - What You See Is What You Need (WYSIWYN) - so creating new slides is easy.

Anyway, I did something similar with TiddlySlides a little while ago, and @FND created a nice Python script to inline external resources - http://mini.softwareas.com/using-fnds-excellent-spapy-to-make-a-single-p. I wanted something slightly different; since this is markup, I can't rely on &lt;img src... pattern. Could have possibly incorporated changes into Fred's SPA, but being that I need it for GDC presentation tomorrow, and I said the last thing to myself the last time I did these slides and it didn't happen, I opted to make a Ruby script which is general-purpose, but meets the specific needs of my slides. See <a href="http://gist.github.com/526114">GIST</a>

[ruby]
#!/usr/bin/env ruby
# This script will download all images referenced in URL (URLs ending in
# jpg/gif/png), stick them in an images/ directory if they're not already there,
# and make a new file referencing the local directory.
#
# The script depends on the http://github.com/nahi/httpclient library.
# 
# USAGE
# localiseImages.rb index.html
# ... will create images/ containing images and local.index.html pointing to them.
#
# The point is to cache images so your HTML works offline. See also spa.py
# http://mini.softwareas.com/using-fnds-excellent-spapy-to-make-a-single-p

require 'httpclient'

### UTILITIES
IMAGES_DIR = 'images'
Dir.mkdir(IMAGES_DIR) unless File.directory?(IMAGES_DIR)
def filenameize(url)
  IMAGES_DIR + '/' + url.sub('http://','').gsub('/','__')
end

def save(filename,contents)
  file = File.new(filename, "w")
  file.write(contents)
  file.close
end

### CORE
def saveImage(url)
  save(filenameize(url), HTTPClient.new().get_content(url))
end

def extractImages(filename)
  contents = File.open(filename, "rb").read
  localContents = String.new(contents)
  contents.scan(/http://S+?.(?:jpg|gif|png)/im) { |url|
    puts url
    saveImage(url) unless File.file?(filenameize(url))
    localContents.gsub!(url, filenameize(url))
  }
  save("local."+filename, localContents)
end

### COMMAND-LINE
extractImages(ARGV[0])
[/ruby]

Aside: This is also related to "offline" web technologies...my article on "Offline" recently went live at HTML5Rocks: <a href="http://www.html5rocks.com/tutorials/offline/whats-offline/">"Offline": What does it mean and why should I care?</a>.