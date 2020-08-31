---
id: 532
title: TiddlyGuv-FOSSology Collaboration
date: 2009-04-13T22:42:17+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=529
permalink: /tiddlyguv-fossology-collaboration/
dsq_thread_id:
  - "375574195"
categories:
  - SoftwareDev
tags:
  - FOSSBazaar
  - FOSSology
  - open source
  - Osmsoft
  - TiddlyGuv
---
I will round out the FOSSBazaar workshop series with some comments on collaboration between TiddlyGuv and FOSSology.

First, what's <a href="http://fossology.org">FOSSology</a>? Simply put, FOSSology in its current state is a code/license scanner. You upload content, like a RedHat ISO, and it recursively explodes it into individual files, also recognising by way of checksums when a file is duplicated (across all the RPMs in a RedHat distro, you will probably see some files appear thousands of times). It then walks through each unique file/archive and tries to determine its license. At the end, you get a report telling you, for example, that the ISO contains 2120 GPL 3 licensed packages, 175 MIT licensed packages, and so on.

The underlying philosophy is to automate the license discovery process. Let developers get on with their job pulling in what they need to, in accordance with their companies policies, and then use the tool to audit what's there. This is in preference to requiring developers to manually declare all that info - and even if they did declare that info, it provides a suitable audit mechanism to check against their report.

TiddlyGuv will eventually keep track of projects and as much as possible, we'd like to automate the process of tracking those projects' components and licenses. Therefore, we'd like to call on FOSSology to capture this info. As a completely orthogonal side benefit, it would be a nice proof-of-concept if two open source projects, each primarily motivated by the needs of the developers' own organisation, could talk to each other.

I was fortunate to meet Mark Donahoe from the FOSSology team at the workshop and discuss how we might get the tools talking to each other, along with my colleague Andrew Back. The first thing to say is we all want to just get some simple proof-of-concept integration happening. This is the agile process at work - a proof-of-concept would help us understand whether it's worth proceeding and may inspire interest from others, as well as project sponsors (at least in the case of TiddlyGuv).

We see a proof-of-concept working like this. TiddlyGuv user creates a new project; server kicks off a FOSSology code scan and updates TiddlyGuv project record with a link to the code scan report. It's as simple as that; in the future, there might be an email notification when the code scan is complete, and other niceties, but for now, this simple story is enough. All of this would take place in the same network by the way; both TiddlyGuv and FOSSology are tools intended to be run by a company inside their own estate (rather than in "the cloud"). If we implement this integration scenario, we will probably run TiddlyGuv and FOSSology on the same box. TiddlyGuv requires Python; FOSSology requires PHP and MySQL. Not the same, but both easily installable on a run-of-the-mill Linux server.

To get this proof-of-concept working, we each have some steps to take.

Osmosoft will need to introduce a project data model, using the TiddlyWeb data structure, and the UI to maintain it. This is the biggest step for us, because we haven't really started that yet. We will then need to introduce a TiddlyWeb plugin that kicks off FOSSology when a new code repository is specified, and to store the resulting scan ID.

On FOSSology's side, we need two things. First, FOSSology would need to allow "upload" of a URL rather than a physical file. i.e. you could just give it the URL of an archive or a SVN URL pointing to the project root within Subversion; and FOSSology would then pull the content from there and treat it as if you had uploaded it. Second, FOSSology's command line mode would need to return the scan ID. I believe this is generated at kick-off time, so it could be returned even though the report isn't yet present. From the scan ID, TiddlyWeb can calculate the scan report URL, which it can store and display in the project's TiddlyGuv page.

Since the project functionality hasn't even begun yet, all this will take a while even to build a rudimentary proof-of-concept, but from last week's meeting, both parties are keen to make it happen.