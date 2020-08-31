---
id: 157
title: 'How It Works: Ajaxian &#8220;Guesstimate&#8221; on ITunes Counter'
date: 2005-07-08T15:54:55+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajaxian-guesstimate-on-download-counter
permalink: /ajaxian-guesstimate-on-download-counter/
"itunes:category":
  - Technology:Computers, Technology:Developers, Technology:Information
  - Technology:Computers, Technology:Developers, Technology:Information
dsq_thread_id:
  - "376210477"
  - "376210477"
categories:
  - HumansAndTech
  - Links
  - SoftwareDev
---
<h2>Ajaxian "Guesstimate" on Apple Homepage</h2>

[The Ajaxian blog](http://www.ajaxian.com/) links to another showcase Ajaxian
application: [An ITunes Counter on the Apple Homepage](http://www.apple.com/). The counter shows the number of songs sold so far. What's interesting is that
**the counter redisplays quickly, every 100 milliseconds, but the remote call
only occurs once a minute**.  The counter is continuously updated with a
*guesstimate* that's good enough for most users, and once a minute has a
rendezvous with reality, as the new results come in from the server.

The concept here is cool, because it works for users even though it seems wrong
from a technical viewpoint. It's fine for users because it conveys the general
feel of ITunes activity. It goes against the mindset of many programmers
because it's guaranteed to be wrong and, even worse, there's the possibility
the counter will go backwards if the estimate overshoots.

**So I've added a ''Guesstimate'' pattern to the [Ajax
Patterns](http://www.ajaxpatterns.org). The Apple demo shows how a Guesstimate
can be used to enhance the standard ''Periodic Refresh'' pattern.**  I'd be
grateful if you can leave a comment on any others you might know of.
Javascript-based countdown/expiration is one example I've seen, simply using
the browser's timer as a proxy for the server's timer.

**I decided to see how the ITunes counter works, so a walkthrough follows.**
Fortunately, the code's really clean and well-commented. Thanks Apple and
Dunstan and Dan (who are mentioned in the comments ... I think Dion@Ajaxian was hinting
it's <a href="http://www.usernomics.com/news/2005/05/ajax-summit-continued-3.html">Dunstan
Orchard</a> :-)). It's nice to see a prominent website not obfuscating its
Javascript.

<h2>Quick Design Overview</h2>

**The server updates only once every five minutes and the browser checks it once a minute. On each update, the browser gets back the most recent sales figure along with the sales figure five minutes earlier. It knows how many songs have been sold in a five-minute period, so it can work out how many are sold every hundred milliseconds. So it repaints the counter every hundred milliseconds, upping it by that increment.**

There are two loops:

   * A quiet loop (<tt>doCountdown()</tt>) calls the server every minute to get new song stats.
   * A vigorous loop (<tt>doCountdown()</tt>) uses rate estimation data to morph the counter display every 100 milliseconds.

The key global variables are <tt>rate</tt> and <tt>curCount</tt>:

  * <tt>rate</tt> is the number of songs purchased per millisecond, according to the stats in the XML that's downloaded each miunte.
  * <tt>curCount</tt> is the counter value.

So each time the server response comes in, <tt>rate</tt> is updated to reflect
the most recent songs-per-millisecond figure. And <tt>curCount</tt> is
continously incremented according to that figure, with the output shown on the
page.

<h2>General Observations</h2>

* It's nice to see a script that's both well-designed and well-documented. Thanks again!
* The script is resilient wrt the outputted XML - it doesn't assume the XML updates every five minutes. It does, however, use [0] and [1] positions to locate current and pre, where it would ideally use the tag attributes. (No biggie, the whole thing's only a temporary promotion anyway.)
* Interesting that they're not using one of <a href="http://ajaxpatterns.org/Ajax_Frameworks">the many XMLHttpRequest wrapper frameworks</a>. Rolling your own requests is probably characteristic of most Ajaxian apps right now.
* The increment-per-millisecond calculations might have been easier if performed on the server-side. I don't know if the authors had complete control, but the ideal thing would be to output a server-side response containing (a) current count and (b) increment per millisecond. I'm all for heavy use of Javascript when it's required, but where there's an app-specific call involved, it may as well take the load off the browser.
* Every five minutes, the extremely observant (borderline-obsessive) user will notice a sudden jump up as the counter is aligned with reality. It's almost always "up" because the rate is deliberately adjusted downward a bit, presumably for this exact purpose. The sudden jump up can only happen at the one-minute checkpoints, so the user would have to be staring at the counter for a minute to see it. It would be fun, though pointless, to design the checkpoint re-alignment to be smoother, e.g. a simple algorithm would be to simply predict where the counter should be in one-minute's time, and base the increment on that figure rather than directly on the current rate. Thus, the adjustment would be amortised over the whole minute.
* The display can only update at 100 millisecond intervals, so you get a bit of
flickering - sometimes an increment, sometimes no change. I could think of two
interesting alternatives: (a) Calculate the interval so that it's roughly the
amount of time a single song is sold in. Then, the counter will smoothly flow
through each number (until the server-side update occurs), which is what you'd
generally expect from a counter. It doesn't have to be exact because the whole
thing's a guess anyway. (b) Make the delay deliberately large, e.g. two
seconds, so people can see how much it's jumped in that time.  But I prefer
(a)!

<h2>Walkthrough</h2>

Note that I've re-formatted some of it. (Markdown Good, Code+Markdown Bad.)

The page's initialisation sequence is set up:

<pre><code>
  addEventToObject(window,'onload',initCountdown);
</code></pre>

So <tt>initCountdown()</tt> is called first. I wish I could verify this, but apparently the price any Mac
user pays for running IE is a static image, while everyone else revels in the Ajaxian
counter movement. (I know.)

<pre><code>
  if ((browser.isIE == true) && (browser.isMac == true)) {
    var counterDiv = (document.getElementById('counter')) ?
      document.getElementById('counter') : null;
    //Put any chunk of HTML in here you wish to be displayed for IE Mac
    var ieMacContent = '<a href="/itunes/500million/">
      &lt;img src="http://images.apple.com/home/
      2005/images/itmscounteriemac20050705.gif"/&gt;</a>';
    counterDiv.innerHTML = ieMacContent;
  } else {
    doCountdown();
  }
</code></pre>

So, for most people, the take-home message is we're going to run
<tt>doCountdown()</tt> on startup, which is a loop that performs a request, then
calls itself a minute later. So it's performing a request every minute:

    //get most recent values from xml and process
    ajaxRequest('http://www.apple.com/itunes/external_counter.xml',
                initializeProcessReqChange);
    //on one minute loop
    var refreshTimer = setTimeout(doCountdown,refresh);

If you visit that link, you'll see the counter XML. This is what will be sent
to <tt>initializeProcessReqChange</tt> once a minute, even though the content
is only updated every 5 minutes:

<pre><code>
  &lt;root&gt;
    &lt;count name="curCount" timestamp="Thu, 07 Jul 2005 14:16:00 GMT"&gt;
      484406324&lt;/count&gt;
    &lt;count name="preCount" timestamp="Thu, 07 Jul 2005 14:11:00 GMT"&gt;
      484402490&lt;/count&gt;
  &lt;/root&gt;
</code></pre>

<tt>initializeProcessReqChange()</tt> does the usual Ajaxian <a href="http://jibbering.com/2002/4/httprequest.html">waiting-for-4-and-200-statuses
thing</a>, and basically passes the result to <tt>setCounters</tt>. On first run, it also
kicks off <tt>runCountdown</tt>:

<pre><code>
  setCounters(req);
  if (XMLHttpRequests < 1 || !countTimer) runCountdown();
</code></code></pre>

<tt>setCounters()</tt> parses the XML request. **It's not just looking for the
current counter value: by comparing the previous and current values, it's
calculating the all-critical <tt>rate</tt> variable, a global which tracks
number of songs per millisecond.**

Let's walk though the calculation. First, we check if there's been a new update
(remember, the XML is only updating every five minutes at present, but this
script is called once a minute). The condition checks if the previous count
correspond to what was recently the current count, ie. if the value has "fallen
through" to become the previous value, in which case a new current value is
reigning:

<pre><code>
  preCount = parseInt(req.responseXML.getElementsByTagName('count')[1].
               childNodes[0].nodeValue);
  //if new values
  if (preCount == initCount || initCount == 0) {
</code></pre>

Okay, something's changed. We have the previous count already, now let's grab everything else we need from the XML:

<pre><code>
  initCount = parseInt(req.responseXML.getElementsByTagName
              ('count')[0].childNodes[0].nodeValue);
  initDate = new Date(req.responseXML.getElementsByTagName
              ('count')[0].getAttribute('timestamp'));
  preDate = new Date(req.responseXML.getElementsByTagName
              ('count')[1].getAttribute('timestamp'));
</code></pre>

Cool, we can then calculate the rate as (number of new songs) / (time elapsed):

<pre><code>
  //calculate difference in values
  countDiff = initCount-preCount;
  //calculate difference in time of values
  dateDiff = parseInt(initDate.valueOf()-preDate.valueOf());
  //calculate rate of increase
      ((songs downloaded in previous time)/time)*incr
  rate = countDiff/dateDiff;
</code></pre>

Next, an adjustment is applied. <b>The adjustment
ensures the guesstimated counter rises a bit slower than we'd expect a real
counter to rise. An underguesstimation is a good thing, because it means
when we next perform a real update using server-side data, there's not much
chance the counter will drop</b>. In general, we'd expect it to jump
up a bit after this alteration, but that's okay, because it will always do jump one way or the other due to
the discrepancy between our guess and reality. The 80% adjustment just
about guarantees the jump is northward, which is more in line with user expectations.

<pre><code>
  rate = rate*0.8;
      //dunstan adjusting the rate down
      // to 80% as per dan's instructions
</code></pre>

What follows is a further adjustment to compensate for the time we've spent in
this method. I'm surprised it's necessary, but the net effect anyway is
that we have set the global current count value, a tiny bit higher than what
was in the XML:

<pre><code>
  curCount = initCount+curCountElapsed;
</code></pre>

So that's the calculation that happens when the counter response comes back.

As well as the once-a-minute server call, there's the
once-every-100-milliseconds counter repaint. <tt>runCountdown()</tt> handles this.
Now that we know about the <tt>rate</tt> variable, it's quite simple to see
what's going on here.  <tt>incr</tt> is the pause between redisplays - 100ms.
So every 100ms, it will simply show the new guesstimate by adding the expected
increment in that time.

<pre><code>
    //multiply rate by increment
    addCount = rate*incr;
    //add this number to counter
    curCount += addCount;
</code></pre>

And finally, morphing the display to show the new guesstimate. Apparently, the
show's over when we hit 500 million downloads, so the counter is only going to
show 500 million at that stage.

<pre><code>
    c.innerHTML = (curCount&lt;500000000) ?
      intComma(Math.floor(curCount)) : "500,000,000+";
</code></pre><!--d44842de11e0df5b065b8c7ac588529f-->