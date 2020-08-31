---
id: 1924
title: Defer and Recur with Rails, Redis, and Resque
date: 2013-07-04T23:44:16+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1924
permalink: /defer-and-recur-with-rails-redis-and-resque/
categories:
  - SoftwareDev
tags:
  - Rails
  - Redis
  - Scheduling
---
<a href='http://www.keepcalm-o-matic.co.uk/p/keep-calm-and-queue-up-4/'><img src='http://i.imgur.com/jMqQmbM.png'></a>

I've put off some scaling related issues about as long as possible, and am now proceeding to introduce a deferred-job stack. I'll explain what I've learned so far, and with the caveat: this isn't in production yet. I'm still learning.

### What it's all about

Tools like Resque let you perform work asynchronously. That way, you can turn requests around quickly, so the user gets *something* back immediately, even if it's just "Thanks, we got your request", which is nicer than the user waiting around 5 minutes, and ensures your server doesn't lock up in the process. Typical example being sending an email - you don't want the user's browser to wait while your server connects elsewhere and fires off the email. Other examples would be fetching a user's profile or avatar after they provide their social profile info; or generating a report they asked for.

So you set up an async job and respond telling the user their message is on the way. If you need to show the user the result of the delayed job, make the clien polls the server and render the result when it's ready. More power XHR!

### The simple way to do this

The simple way, which worked just fine for me for a long time and I'd recommend for anyone starting, is a simple daemon process. Basically:

[ruby]
  while true
    if (check_database_for_condition)
      do_something
    sleep 10
  end
[/ruby]

### The fancy way

The problem with the simple way is it can be hard to parallelise and monitor; you'll end up reinventing the wheel. So to stand on the shoulders of giants, go install Redis, Resque, and Resque-Scheduler. I'll explain each.

#### Redis

[Redis](http://redis.io/), as you probably know, is a NOSQL database. It's been described as a "data structure server" as it stores lists, trees, and hashes; and [assuming Knuth is your homeboy](http://www.flickr.com/photos/ioerror/3014911710/), that's a mighty fine concept. And it's super-fast because everything is kept in memory, with (depending on config) frequent persistence to disk for durability.

#### Resque

[Resque](https://github.com/defunkt/resque) is no sneezing matter either, being a tool made and used by GitHub, no less.

Resque uses Redis to store the actual jobs. It's worth explaining the main components of Resque, because I've found they're often not defined very clearly and if you don't understand this, everything else will trip you up.

*Job.* A job is a task you want to perform. For example Job 1234 might be "Send welcome email to joe@example.com". In Resque, a job is defined as a simple class having a "perform" method, which is what does the work [1].

*Queue.* Jobs live in queues. There's a one-liner config item in the Job class to say which queue it belongs to. In a simple app, you could just push all jobs to a single queue, whereas in a bigger app, you might want separate queues for each job type. e.g. you'd end up with separate queues for "Send welcome email", "Fetch user's avatar", and "Generate Report". The main advantage of separate queues is you can give certain queues priority. In addition to these queues, you also have a special "failed" queue. Tasks that throw exceptions are moved to "failed"; otherwise the task disappears.

*Worker.* A worker is a process that runs the jobs. So a worker polls the queues, picks the oldest jobs off them, and runs them. You start workers via Resque's Rake task, and in doing so, you tell it which queues to run. There's a wildcard option to run all queues, but for fine-grained optimisations, you could set up more workers to run higher-priority queues and so on.

An important note about the environment. Rails' environment can take a long time to start, e.g. 30 seconds. You clearly don't want a 30-second delay just to send an email. So workers will fork themselves before starting the job. This way, each job gets a fresh environment to run off, but you don't have the overhead of starting up each time. (This is the same principle as Unicorn's management of Rails' servers.) So starting the worker *does* incur the initial Rails startup overhead, but starting each job doesn't. In practice, jobs can begin in a fraction of a second. You can further optimise this by making a custom environment for the workers, e.g. don't use all of Rails, but just use ActiveRecord, and so on. But it's probably not worth the effort initially as the fork() mechanism gets you 80% there.

#### Resque-Scheduler

For many people, Resque alone will fit the bill. But certain situations also call for an explicit delay, e.g. "send this email reminder in 5 days"; or repeat a task, e.g. "generate a fresh report at 8am each day". That's where [Resque-Scheduler](https://github.com/bvandenbos/resque-scheduler) comes in [2].

Resque-Scheduler was originally part of Resque, so it basically extends the Resque API. The "scheduling", i.e. repeated tasks, are represented as a Cronjob-like hash structure and can be conveniently represented in a YML file.

Delayed jobs are created by your application code. It's basically the same call as when you add the job directly to Resque, but you need to specify an additional delay or time argument.

The cool thing is jobs are persisted into Redis, so they will survive if the system &mdash; or any components (Redis/Resque/Resque-Scheduler) &mdash; goes down. I was confused at first as I thought they were added to some special Resque queue. But no, they are actually in the Redis database. I found this by entering `keys *` into Redis's command-line tool (redis-cli), which yielded some structures including "resque:delayed:1372936216". When I then entered `dump resque:delayed:1372936216`, I got back a data structure which was basically my job spec, ie. `{class: 'FeedHandler', arg: ['http://example.com']`.

So Resque-Scheduler basically wakes up every second or so, and does two things: (a) polls Redis to see if any delayed jobs should now be executed; (b) inspects its "schedule" data structure to see if any repeated jobs should now be executed. If any jobs should now be executed, it pushes them to the appropriate Resque queue.

### Notes

1. Conceptually a job definition is little more than a function definition, rather than a full-blown class. But being a class is the more Rubyesque way to do it and also makes it easy to perform complex tasks as you can use attributes to hold intermediate results, since each job execution will instantiate a new job object.

2. I evaluated other tools, e.g. Rufus and Clockwork, but what appeals about Resque-Scheduler is it persists delayed jobs and handles both one-off and repeated jobs.