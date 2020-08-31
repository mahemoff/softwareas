---
id: 2268
title: 'Horizontally scaling databases: MySQL/Postgres Sharding'
date: 2017-01-17T13:15:39+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2268
permalink: /horizontally-scaling-databases-mysqlpostgres-sharding/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"c9b8698bf0ec";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:41:"https://medium.com/@mahemoff/c9b8698bf0ec";}'
categories:
  - Uncategorized
---
At some point, a single database instance starts to creak as more objects are added to it, even with read-only replication. A battle-proven strategy here is to scale horizontally via sharding, however there be dragons. Here are general design principles on sharding with relational databases such as MySQL and Postgres.

These are some good case studies on MySQL sharding:

* [Sharding Pinterest: How we scaled our MySQL fleet](https://engineering.pinterest.com/blog/sharding-pinterest-how-we-scaled-our-mysql-fleet) (+ [Hacker News thread on this](https://news.ycombinator.com/item?id=10086782)).
* [Sharding & IDs at Instagram
](http://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram)

* **Only shard when you have to.** Premature optimisation is, after all, [the root of all evil](http://wiki.c2.com/?PrematureOptimization). Sharding adds more servers to build, maintain, failover, and backup; and it makes apps more complex.
* **Each object/record has its own GUID to uniquely identify it across all servers.** The GUIDs indicate the shard this object lives in. When requests come in, they specify a GUID which the server can then map to a particular shard. [Instagram Engineering](http://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram) has a good overview on GUID generation, there are various options with pros and cons.
* **Use many virtual shards and distribute evenly between them.** It's best to assign each object to one of thousands of virtual shards, and then map those to physical shards (ie database instances running on a particular host). e.g. You might assign an object to shard 1331 out of a possible 10,000 shards, using a simple random number or modulo function to ensure each shard has approximately the same quantity. This virtual shard its permanent home and will never change. You then map 1331 to "database server 3". The reason for this indirection is so you can easily split up data as the system grows.
* **Related content lives in the same shard.** Typically, content owned by a single user/team/company should live together on the same (virtual) shard. For many applications, the main queries that need a quick user response are all within the same object graph, ie some kind of join between a company, its workers, and their content. It makes sense to store all of this in the same shard, so if you have a natural hierarchy, ensure each class's shard is initialised with that of the root class (e.g. each "sale" is assigned to the same shard as the shard of the "salesperson" who made them, and each "salesperson" is assigned to the same shard as the "company" they work for).
* **Slave replication is only for backup/failover.** This is advocated by he Pinterest paper. Replication can cause weird "time travel" bugs, where an application reads stale data from a slave and then uses it to update the master. Sharding is sufficient to replace the performance benefits of reading from multiple slaves, so replication should only be used for backup and failover purposes. Each shard (and any central database) gets its own slave.