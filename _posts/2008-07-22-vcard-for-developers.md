---
id: 464
title: vCard for Developers
date: 2008-07-22T22:28:17+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=461
permalink: /vcard-for-developers/
dsq_thread_id:
  - "375164990"
categories:
  - SoftwareDev
tags:
  - hCard
  - PIM
  - standard
  - Tutorial
  - vCard
  - Web
---
<a href="http://www.frederiksamuel.com/blog/images/poul_nielsen.jpg"><img width="350" src="http://picupper.com/2008/07/22/poul_nielsen.jpg" /><a>

I've been researching vCard for a project involving contacts management. This is a quick overview on vCard aimed at developers, with a demo and stealing the example from <a href="http://en.wikipedia.org/wiki/VCard">wikipedia's vCard entry</a>. <a href="http://tools.ietf.org/html/rfc2426#section-3.1.1">The official standard is here</a>.

<img>

<h2>The Format</h2>

vCard is a standard for representing contact information, the kind of info you would see for a contact in an address book or email application - name, address, and so on. By convention, the file suffix is ".vcf". The info is represented in a text file format as shown below:

<pre>
BEGIN:VCARD
VERSION:2.1
N:Gump;Forrest <i>(Name)</i>
FN:Forrest Gump <i>(Full Name)</i>
ORG:Gump Shrimp Co.
TITLE:Shrimp Man
TEL;WORK;VOICE:(111) 555-1212
TEL;HOME;VOICE:(404) 555-1212
ADR;WORK:;;100 Waters Edge;Baytown;LA;30314;United States of America
LABEL;WORK;ENCODING=QUOTED-PRINTABLE:100 Waters Edge=0D=0ABaytown, LA 30314=0D=0AUnited States of America
ADR;HOME:;;42 Plantation St.;Baytown;LA;30314;United States of America
LABEL;HOME;ENCODING=QUOTED-PRINTABLE:42 Plantation St.=0D=0ABaytown, LA 30314=0D=0AUnited States of America
EMAIL;PREF;INTERNET:forrestgump@walladalla.com
REV:20080424T195243Z
END:VCARD
</pre>

As you can see, the format is an ugly mainframe-style format that belies vCard's 1995 birthdate. If it was created a year or two later, it likely would have been <a href="http://www.xmpp.org/extensions/xep-0054.html">a prettier XML format</a>. But don't be scared, it's mostly harmless. You basically have field-value pairs separated by ":". The standard defines all possible fields and the format for their values.

<a href="http://blog.jempp.com.au/labels/weird%20promotional%20items.html"><img src="http://picupper.com/2008/07/22/fronttennis08.jpg" width="400" /></a>

<h2>The Fields</h2>

The fields defined are: FN (full name - e.g. "Mr. Homer J. Simpson"), N (name - e.g. "Simpson;Homer"), NICKNAME, PHOTO, BDAY (birthday), ADR, LABEL, TEL, EMAIL, MAILER, TZ, GEO (lat/long co-ordinates), TITLE, ROLE, LOGO, AGENT (e.g. a secretary or personal assistant - this is a recursive vCard instance!), ORG, CATEGORIES, NOTE, PRODID (which product created the vCard), REV (a revision ID for this vcard instance), SORT-STRING (the "primary key" on which this record should be sorted, e.g. if you want 'Van Winkle' to be sorted as 'Winkle'), SOUND, URL, UID, VERSION (the version of vCard used to generate this vCard), CLASS (a security access level for this vCard instance - e.g. is it public, protected, private?), KEY (a public key, e.g. you could use it if you wanted to send the contact something encrypted). The only mandatory fields here are FN and N (the two most obscurely named fields, naturally ;)).

Each field-value pair is something like a database record or an object instance, insofar as it includes a number of values. I guess the standard could have avoided this by defining 200 different field names, but instead they grouped related attributes together into the same field. So you end up with just a single "name" field ("N"), which is actually an aggregation of several fields. e.g. " N:Stevenson;John;Philip,Paul;Dr.;Jr.,M.D.,A.C.P." contains surname, first name, other names, title, and honorifics.

Similarly, field names are not always just a single word, but can also be qualified by type. Therefore "TEL;WORK;VOICE;PREF" is equivalent to "TEL;TYPE=WORK,VOICE,PREF" and also "TEL;TYPE=WORK,TYPE=VOICE,TYPE=PREF". (The first form actually appears in the wikipedia example, but the standard talks about the second and third form, so any parser would have to read all of them.). The multiple types are effectively tags/keywords, i.e. the telephone number here is at once a work number, a number supporting voice interaction, and a preferred usage number.

Fields like logo and photo can either be a URL or binary data embedded directly in the VCARD.

<a href="http://tools.ietf.org/html/rfc2426#section-3.1.1">See the official standard for full details.</a>

<a href="http://www.ubergizmo.com/photos/2007/5/usb-business-card.jpg"><img src="http://picupper.com/2008/07/22/usb-business-card.jpg" width="350" /><a>

<h2>MIME Gubbins: How to Serve vCard from your Web App</h2>

If you ever show contacts in your web app, it's polite to include a vCard export option as users will appreciate the ability to pluck it off the site and into their preferred desktop app. I found serving it to be remarkably easy.

<a href="http://mahemoff.com/project/vcard.phtml">The demo is here</a>

<pre>
&lt;?
  header('Content-Type: text/x-vcard; charset=utf-8');
  header('Content-Disposition: attachment; filename="vcard-example.vcf"');
?&gt;
BEGIN:VCARD
VERSION:2.1
N:Gump;Forrest
FN:Forrest Gump
...
etc
....
END:VCARD
</pre>

See? Just output those two headers, then bust out the vCard. The demo successfully opens in Apple Address Book and MS Outlook.

<strong>Apple Address Book</strong>

<img src="http://picupper.com/2008/07/22/forrestapple.jpg" width="350"/>

<strong>MS Outlook</strong>

<img src="http://picupper.com/2008/07/22/vcard-opi.PNG" width="350"/>

 So it works if you're a Mac or a PC. Neat-O.

<h2>Portability, Limitations, and Variations</h2>

The great thing about standards is there are so many to choose from, as many a cynic has observed. The other great thing about most standards is they give you so much room for creativity, as this cynic responded.  vCard is no exception and can be interpreted in different ways (whether or not these ways conform to the spec I don't know, and is not especially relevant for real-world developers).

In particular, some people think a vCard file can include only one record, while others think it can include any number of records. I made a second demo to test this. <a href="http://mahemoff.com/project/vcard2.phtml">The two-card demo is here</a>. It contains one VCARD after another, as shown below. Well, Apple Address Book likes it and opens up both contacts, while MS Outlook ignores the second. So there.

<pre>
&lt;?
  header('Content-Type: text/x-vcard; charset=utf-8');
  header('Content-Disposition: attachment; filename="vcard-example.vcf"');
?&gt;
BEGIN:VCARD
VERSION:2.1
N:Gump;Forrest
....
END:VCARD
BEGIN:VCARD
VERSION:2.1
N:Fump;Gorrest
....
END:VCARD
</pre>

Furthermore, there are "extensions", which are new property types that go beyond the standard and are used by certain applications. Wikipedia identifies a veritable menagerie of extensions, including such species as X-MANAGER for manager details; X-AIM/X-MSN/X-ICQ/X-GADUGADU (awesome!)/etc for IM details, and X-ASSISTANT for assistant details (they probably forgot about the AGENT property). any other properties are prefixed with the company who introduced them, leading to the elegantly named X-FUNAMBOL-YOMIFIRSTNAME property (this will soon become the sixth page on the internet to use that term).

<a href="http://beth.typepad.com/beths_blog/bloghercon/index.html"><img src="http://picupper.com/2008/07/22/my_bizcard_collection.JPG" width="400" /></a>

<h2>Related Standards</h2>

vCard is closely related to a wider standard around directory formats, <a href="http://tools.ietf.org/html/rfc2425">RFC 2425</a>. This standard defines the basic, mainframe, field-value pair structure, as well as some basic types - SOURCE (source for the record, e.g. an LDAP server), NAME (name of the record, which will usually be the same a the vCard "N" field), PROFILE (vaguely defined as something about "how the record will be used"), BEGIN, END. BEGIN and END naturally appear in all vCards, but examples I've seen don't use the other three types.

<a href="http://www.w3.org/TR/vcard-rdf">This W3C note</a> attempts to XMLise vCard within an RDF framework.

<a href="http://microformats.org/wiki/hcard">hCard</a> attempts to HTMLise vCard as part of the more-lightweight-than-RDF microformats initiative. (<a href="http://microformats.org/wiki/hcard-examples">examples</a>).

<a href="http://en.wikipedia.org/wiki/ICalendar">iCalendar</a>, aka iCal and formally vCal (which sounds like vCard doesn't it?) came from the Versit consortium around the same time as vCard...both intended for similar types of applications. iCal is about exchanging event information.

<img src="http://picupper.com/2008/07/22/american-psycho-splash.jpg" width="350" />