---
id: 2250
title: Taming Ansible with a control script
date: 2016-05-14T03:37:16+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2250
permalink: /taming-ansible-with-a-control-script/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"81bd228baf1a";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:41:"https://medium.com/@mahemoff/81bd228baf1a";}'
categories:
  - Uncategorized
---
Ansible is very useful for managing multiple servers, but one of its weak points is lack of control over sequencing tasks.

The basic assumption is that you can execute all tasks because it embraces the principle of idempotency. If you add a new task, you should just be able to run the whole playbook again and there will be no side effects because all the other tasks are idempotent.

While that's true in theory, there are many reasons why you'd want to run only a subset of a playbook:

* Most importantly, performance. Some stuff can be slow. Even checking state, to prevent actually making any changes, can be slower than you'd like. Just a second delay for a playbook of 60 tasks would mean waiting a minute every time you want to do something.
* While developing playbooks, it's helpful for debugging purposes to execute only a subset of tasks. (Also, see previous point on performance. You don't want to wait a minute to find out you had a typo.)
* Some tasks should not be done by default. e.g. you may need to restart servers periodically to detect a memory leak. This would have to be "forced" because normally you'd just have a "service" rule indicating the server is "started". So no action would take place because the server is already running, whereas what you need is a separate rule indicated the server is "restarted".

Ansible's primary answer to this is tags - you can specify a list of commands to be run by calling ansible-playbooks with a ----tags argument, and you can skip over other tasks using --skip-tags. These are useful, but limited, mainly because you can't say "this task should only be executed if it's tagged". Yes, you can skip over it with skip-tags, but it will be run by default. e.g. if you have a "restart server" task, it will always be run as part of the standard playbook execution, unless you remember to skip it. Cumbersome.

The common workaround for this is to introduce another concept: variables. Instead of tagging such tasks, you make them happen only when some variable is true. And then default the variable to false. This works well, but things have suddenly got quite confusing to follow. The playbook is now an obstacle course where, for any given task, we have to figure out how to delicately step around some tasks while executing others.

For this reason, I've concluded the best approach is to make a front-end control script. It can't be a "top-level" playbook, because another limitation is that playbooks can't execute tagged or skip-tagged tasks. So it's a plain-old bash script. I'm building up all typical invocations of Ansible in this control script.  Every time I want to invoke Ansible, I ensure there's a specific function present. Over time, I'll be able to consolidate these and adjust the underlying playbooks as necessary.

<script src="https://gist.github.com/mahemoff/5febd49128dfa5cae24243968f2289c4.js"></script>

It's invoked like: `./control.sh staging load_balancers`