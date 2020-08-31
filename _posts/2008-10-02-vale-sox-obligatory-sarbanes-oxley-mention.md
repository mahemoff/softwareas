---
id: 489
title: Vale SOX? Obligatory Sarbanes-Oxley Mention
date: 2008-10-02T16:27:42+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=486
permalink: /vale-sox-obligatory-sarbanes-oxley-mention/
dsq_thread_id:
  - "375573976"
categories:
  - HumansAndTech
tags:
  - Finance
  - SOX
  - Standards
---
<a href="http://www.allbusinessschools.com/faqs/forensic-accounting.php"><img src="http://picupper.com/2008/10/02/money.jpg" style="float: right; margin: 10px;" /></a>

I can't let the current credit crunch / financial crisis / Wall St meltdown pass without mentioning <a href="http://en.wikipedia.org/wiki/Sarbanes-Oxley_Act ">the Sarbanes-Oxley Act</a>, aka SOX.

I feel compelled to do so because I haven't seen it mentioned once in the mainstream media during the past fortnight of turbulence, and yet it should have at least played some role in reducing the likelihood and impact of an event like this. Otherwise, it was a waste of effort.

Searching <a href="http://news.google.com/news?hl=en&nolr=1&q=sarbanes-oxley&btnG=Search">Google News for "Sarbanes-Oxley"</a> just now yielded about a half-dozen results. One is from 2006, one is a letter, one is about <a href="http://weblogs.baltimoresun.com/news/local/rodricks/blog/2008/09/why_sarbanes_voted_yay.html">Sarbanes' son's bailout vote</a>. Not much. The <a href="
http://business.smh.com.au/business/tide-of-economic-fortune-revealed-by-a-hindrance-or-a-help-20080926-4oyi.html?page=2">only relevant article</a> I found:

<blockquote>
The pain felt in middle America was so intense that Congress enacted legislation to clamp down on such errant behaviour. The Sarbanes-Oxley Act of 2002 imposed stricter levels of disclosure on public company boards, management and accounting firms. It was hailed at the time as a breakthrough in regulating errant corporate behaviour. But it should come as no surprise that about a year ago, during the height of the most recent boom, US regulators were coming under intense pressure to dilute parts of the legislation.

Sarbanes-Oxley, the argument went, had cost Wall Street its coveted position as the world's financial hub. The high cost of compliance with the legislation had seen international focus shift to London.
</blockquote>

The article goes on to explain why it might be not so relevant to the current situation, which is completely dominated by the banks:

<blockquote>
The latest crisis has emerged from a different area - the lax prudential regulation of America's banks. Housing loans were pushed on to people who had a history of default. That's the definition of subprime.
</blockquote>

So it's not a case of "this is exactly the kind of thing SOX was meant to prevent". It's more subtle than that - SOX is only public companies, and not all banks are public; SOX covers all types of companies, not banks which have particularly complex financial characteristics; SOX is about control and reporting, and does not place specific constraints on levels and forms of credit risk.

Nevertheless, many banks are public companies and public companies must comply with SOX (even if the system is developed in the UK...as long as it operates in the USA, it must comply, that's my legally dunce understanding of the matter). Sarbanes still applied in banks from around 2003. I was working on one project where "pulling up your SOX" was a constant non-functional force lurking in the background of many major design decisions. So, for example, if we were to choose an in-memory database, what would happen to the auditing facility in the event of a sudden crash, would this cause a violation of SOX?

Another system I was looking at working on involved the treasury operation of a prominent American bank, where SOX was a big driver for them to streamline the performance of the system that comes out with a single, very important number: the bank's overall position.

It's vastly beyond the scope of this blog to explain away the crisis or even SOX's (non) effect on it. What I can say, though, from a software perspective is that it feels like yet another standard that's complex enough, and enforced enough, to drive substantial effort, while being high-level enough to not necessarily be very useful, at least not in cases where the intent was already there.

Alistair Cockburn wrote to the effect, "show me the methodology, and I'll show you the methodologist's fears". We might well apply this to standards and regulations too. 

SOX can be very closely tied back to Enron and related collapses and the fear of a repeat incident. However well-intentioned, there are two problems with standards that emerge from fear: (a) forcing someone to not follow the same strategy as that which led to a collapse...is no way to guarantee a similar collapse won't take place again, for there are many alternative strategies they may take; if you retrospectively try to do what would have prevented recent incidents, you can expect your standard to be gamed hard by those using alternative strategies; (b) even if you can prevent a repeat incident, at what cost? Many times, the constraints you place on creativity and the degree to which your standard crushes human spirit and consequently inhibits progress, these costs may well outweigh the benefits.

Whether these problems were causes by SOX is a topic for debate. But as the world readies itself for a whole new set of controls - many of which will affect your daily work and mine, dear software reader - one can only hope there is big ups on some fair dincum contemplation and ixnay on the knee jerk, eh.