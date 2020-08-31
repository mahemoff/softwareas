---
id: 2235
title: How to show dates to humans
date: 2016-04-03T09:48:29+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2235
permalink: /how-to-show-dates-to-humans/
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:68:"https://cdn-images-1.medium.com/fit/c/200/200/0*8ZyBPj8z4gUV0dfA.jpg";s:10:"author_url";s:28:"https://medium.com/@mahemoff";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"478ca35c4d7d";s:21:"follower_notification";s:2:"no";s:7:"license";s:8:"cc-40-by";s:14:"publication_id";s:2:"-1";s:6:"status";s:5:"draft";s:3:"url";s:41:"https://medium.com/@mahemoff/478ca35c4d7d";}'
categories:
  - Uncategorized
---
First, how not to show them:

"Hey come to our amazing concert &mdash; 5/6!"

Now, how to show them:

"Hey come to our amazing concert &mdash; Wednesday May 18, 2016!"

I admit the former is more concise, bt cncs dsnt lwys mn bttr even if you can parse it.

The rules are simple, please do this when you mention a date:

1. **Include the year.** There are [80 trillion web pages](https://twitter.com/kevin2kelly/status/715569362279600128) and most of them were written before a few months ago, so if I see a date without context, I have no evidence it refers to a time in the future. It could be any time in the last 2 decades.
2. **Name the month.** Let's not get involved [in a big debate](http://softwareas.com/no-lets-not-use-that-date-format/) about MMDD versus DDMM versus YYYYMMDDAAAA🙏🙏🙏🙏ZZZZzzzz. When we're displaying dates to regular users, keep it simple and use a format everyone immediately understands - the month name. Or an abbreviation thereof. I realise that's not international-friendly, but the date presumably appears with surrounding text, so use the same language for the month and use one of many i18n frameworks to localise it if you have multiple languages. [1]
3. **Name the weekday.** Come on, would it kill you to tell me what day this is on as well? That's a big deciding factor for many people and helps to plan for the event and remember exactly when it happens.
4. **Count it down.** Here's where digital formats can better traditional printed formats. The date display can be dynamic, so you can show a countdown when it's appropriate. Again, it helps to make the date more meaningful and can also create some excitement around the event.
5. **Add to calendar.** In some cases, you might provide support for adding the date to users' calendars. There's unfortunately no great standards for this, but there are [tools](http://addtocalendar.com/).

Any others?

1. Credit [Daniel](https://twitter.com/DanielBaird/status/716389733559967744) for the reminder.