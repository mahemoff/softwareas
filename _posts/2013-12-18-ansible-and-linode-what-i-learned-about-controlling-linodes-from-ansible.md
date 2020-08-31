---
id: 1935
title: 'Ansible and Linode: What I learned about controlling Linodes from Ansible'
date: 2013-12-18T16:11:17+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1935
permalink: /ansible-and-linode-what-i-learned-about-controlling-linodes-from-ansible/
categories:
  - SoftwareDev
---
## Background: Learning Ansible

I decided it's time to bite the bullet and commit to a configuration management platform. Ansible keeps coming up as the present pinnacle. There were a few hurdles before I could get to the point of successfully rebooting a Linode, so figured I'll save you the learning curve.

I've not used Puppet or Chef or Salt in production, so I'm not qualified to compare. I can only go by what others say, and apparently Ansible's main strength stems from the fact it ships "with the kitchen sink" instead of forcing administrators to trawl through GitHub to find the appropriate third-party module, which might then be buggy or out of date. And also because it's relatively simple, having a "push" model which simply uses ssh to update remote servers instead of running some agent on them to "pull" changes from the config server. It also supports deploying new apps (like Capistrano) as well as the main purpose of configuring servers.

If you're learning Ansible, I recommend setting up a dedicated VPS to run Ansible and another couple of dummy VPSs to act as the remotes. You could do this cheaply with DigitalOcean for example. And then following the official tutorials. 

## Installing Linode-Python

The first thing to know is that Ansible ships with a vast array of [built-in modules](http://www.ansibleworks.com/docs/modules.html),  *but* not their dependencies. So running an ansible Linode command (`ansible remote-host -m linode somearg=someval'), I got a dependency fail: ["linode-python required for this module"](http://stackoverflow.com/questions/20654401/ansible-required-for-this-module-dependency-issue-with-linode-module).

Easy enough fix, right? Well, I went through various steps to install linode-python and verified it worked by opening the Python repl (ie typing python on the command-line) and entering "import linode". Worked fine.

But same error with Ansible. "linode-python required for this module". I thought my PYTHONPATH must be messed up or ... who knows? Read on ...

## Prepare "localhost" host so you can run local actions

Looking more closely at [the Linode module doc](http://www.ansibleworks.com/docs/modules.html#linode), I realised this is a local action. That is, it doesn't actually run on a remote machine. Which makes sense, because we're trying to run general Linode commands. So it's like a global command, and Ansible's way of dealing with that is to consider it runs on localhost.

So how do you run a local command on the command-line (since I was in experimental mode)?

First, Open up the inventories file (/etc/ansible/hosts) and enter a new group:

    [local]
    localhost

Second, make sure you can ssh to localhost. Which might need you to do this:

    cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

Anyway, just check `ssh localhost` actually works.

## Figure out Linode IDs

At this point, I could use the Ansible Linode module, but I still had a problem changing Linode state. I found the library needed a Linode ID argument, which had to be numeric. This is painful as the Linode web console only shows you the string "nickname" and not its underlying ID.

So I tried to use the API to list IDs, and discovered the Linode Ruby library doesn't actually show those IDs. But turns out, the Python Linode library *does* produce the IDs! I wrote a script to show the ID for each Linode:

<script src="https://gist.github.com/mahemoff/8024734.js"></script>

UPDATE Feb 2014: Actually this isn't necessary as Ansible's dynamic inventory script can do it. Download and run this script to get your list of Linodes: https://github.com/ansible/ansible/blob/devel/library/cloud/linode. It's probably a good idea to just clone that whole ansible project so you can easily access parts of it.

## Bouncy Bounce! Restart the Linode ...
 
Okay, finally I can run this. I found another little quirk is that the module requires a name argument, even though it should be able to work it out from the ID. (It seems to be a bug, as it should only need the name if it's creating a new node, but what do I know.)

    ansible localhost -m linode -a "linode_id=123456 name=funkyserv state=restarted wait=true api_key=$LINODE_API_KEY"

This now works and responds with a "restarted" status. I've verified with the Linode web console the node is actually rebooting.

## Appendix: Bonus tips

I found it useful to refer to the source for the Ansible module. It was easy to find using `locate linode`, located at /usr/share/ansible/cloud/linode and easy enough to follow without having seen a module's internals before.

I got a similar error with the mysql module ("linode-mySqlDb required for this module"). A bit confusing as this turned out to be a different cause. In this case, it really was a remote command, meaning the Python module (and Python itself) would have to be installed on the remote server (ie the mysql server).