---
id: 2200
title: Bloom Filters and Recommendation Engines
date: 2015-11-01T09:07:45+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2200
permalink: /bloom-filters-and-recommendation-engines/
categories:
  - Uncategorized
---
I'll explain here what Bloom filters are and how you might find them useful for recommendation engines. I haven't used them yet in production &mdash; just sharing what I've been learning.

### Why Bloom Filters?

I was thinking about recommendation system algorithm. Not the main algorithm: how do you generate good recommendations. But instead, an important "side algorithm": how do you keep track of recommendations users have previously dismissed? All the genius recommendations in the world aren't going to matter if you keep showing the same results.

The most obvious solution here would be to track everything. Simply store a new record for every "dismissal" the user makes. But that's a lot to store in a high-scale system, e.g. if 10 million users dismissed 20 items each, you have 200 million records to store and index.

So this is where Bloom filters come in as a highly compressed way to store a set of values. The catch is: it's fuzzy. It's not really storing the set; instead, it's letting you ask the question you want to ask, which is: "Is X in this set?" and coming back with a probabilistic answer. But that's okay for something like a recommendation system.

Here's an example. A user Jane has dismissed three articles, identified with their IDs: 123, 456, 789.

Under the traditional model, we perform a standard set inclusion check (e.g. check if a database row exists) and come out with a definite answer:

<pre>
Jane:
  123
  456
  789

Q: Is article 888 in the "Jane" set?
Algorithm: Check if 888 is in [123, 456, 789]
A: No. I'm sure about that.
</pre>

Under the fuzzy Bloom filter model, we end up with some funny value as a fuzzy representation of the whole set, and then we can get a probabilistic answer about set inclusion.

<pre>
Jane:
  01101001 (this is the Bloom filter)

Q: Is article 888 in the "Jane" set?
Algorithm: Check against the Bloom filter (details below)
A: Probably not. But maybe. About 5% likelihood it's in the set.
</pre>

### Deriving the Bloom filter

So in the previous example, how did we end up with that representation of the set (what I playfully refer to as 01101001). And what did we do with it?

It's fairly simple. Remember, this is the only thing we store and the set builds up over time. So the Bloom filter starts out as empty and each new set member adds something to it.

The real representation is a bitwise vector, let's go with 8 bits:
00000000

So when user Jane is created, her Bloom filter is 0000000.

Jane dismisses article 123. Now what we do is, we compute some hashes of 123 using different algorithms. Since we have decided to make our Bloom filter 8 bits, each hash algorithm should give a number between 0 and 256, so we can store the result. Let's assume we use two hash algorithms to hash 123. One ends up with 64 (01000000) and the other with 33 (00100001). So now our Bloom filter is:

01100001

When we get a 1, we set the bit to 1. When we get a zero, we do nothing. So yes, over time, this will fill with 1s. That's why we have to choose a big enough bloom filter size.

Going on, the next dismissal is 456. And maybe we end up with hash values 01001001 and 0110000. So the first of these has added a new "1" to our previous value of 011000001:

01101001

And finally, we might end up with 01001000 and 00100000 for ID 789, neither of which light up any new bits. So we still have the same Bloom filter as before.

01101001

### Is X in the set?

Now we have Jane's Bloom filter, 01101001. This is a fuzzy representation of [123, 456, 789]. We can then ask, for any given value, is it in the set?

e.g. if our recommendation algorithm comes up with 888, should we show it to Jane. We don't want to show it if it is in that set of previous dismissals. We compute using the same hash algorithms as before and perhaps we end up with 00101100. It lit up a different bit (the 6th one), so we can say categorically, it's not in the set. We know that for sure because if it was in the set, all those bits would be on. We know for sure it's not in the set of dismissals, so we can confidently recommend it to Jane.

Take another recommendation we might end up with - 456. Do we show it to Jane? Well, is it in the set of previous dismissals? We compute and get 01101001. It fits within our Bloom filter, so there's a good chance it was in the list of values that was used to build up the filter. But no guarantee. We might end up with a value of 00001000 for another ID, e.g. 555. This would also fit the Bloom filter and we can be no more certain that it was in the original set than we can be for the 456 value. So, it's probabilistic. You can be certain some things aren't in the set, but you can't be certain something was in the set. For a recommendation of 456 or 555, we can't be sure. So in either case, we will *not* show Jane the recommendation and look deeper for more certain values.

### Fine tuning

The example above just magically decided to use a Bloom filter of 8 and hand-waved around the algorithms. In practice, you will need to decide on those things and in practice it will probably be hundreds or thousands of bits; otherwise, every bit will quickly fill up to become 1. A cool thing is that [there are precise calculations](http://hur.st/bloomfilter) that can help you estimate exactly how big the Bloom filter should be, based on the expected number of items in it, combined with your tolerance for error. (If your algorithm can easily generate lots of good recommendations, you could have quite a high tolerance because it would be easy to skip over any potential matches.)

### References

Considering the recommendation problem made me recall [this article about how Medium uses Bloom filters](https://medium.com/the-story/what-are-bloom-filters-1ec2a50c68ff#.v1myeyr3e) and also led me to a useful [tutorial on the topic](http://billmill.org/bloomfilter-tutorial/).