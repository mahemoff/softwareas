---
id: 100
title: 'BNP Reconciliation Notes: Romilly Cocking at BNP Paribas'
date: 2005-04-16T23:22:58+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=100
permalink: /bnp-reconciliation-notes-romilly-cocking-at-spa-2005/
dsq_thread_id:
  - "424125916"
  - "424125916"
categories:
  - SoftwareDev
---
Romilly Cocking gave a 75-minute presentation about his work at BNP Paribas, using agile techniques to implement a reconciliation engine. Unusually for a bank, it's fine with this information being public and Romilly said it would be fine to write about it here.
## The Reconciliation Problem
                                                                                
Reconciliation: Comparing and contrasting two sets of records that should tell
the same story. To detect fraud or error. e.g. A well-organised [ie
[rare/fictitious] person would compare bank statement against chequebook.
Note that we're not talking about matching (subtle differences).
                                                                                
Steps in reconciliation:

+ Read
+ Select
+ Transform
+ Link
+ Compare
+ Report

## SmartRec Development
                                                                                
Wrote SmartRec as a proof-of-concept. Thus, was able to choose the tools and techniques. Used: Java, Eclipse, JUnit, JMock, XMLUnit, XStream, Jaxen, SmartArrays. Methodology was agile. Basically, XP, but with one developer. Used stories; TDD; automated functional tests - easy in this domain because no UI, inputs and outputs are XML files; close interaction with user; weekly reviews.
                                                                              
## Technical Issues

Used SmartArrays because it's based on APL, which Romilly has a lot of
experience with, and was confident it would provide a neat solution. Did encounter some impedance mismatch: Switch between two mindsets: thinking in arrays versus
thinking in objects. Ended up exposing arrays more than required. So code too
closely coupled to arrays. Realised mistake, but pairing would probably have caught it straightaway.

Specifying reconciliation definition in XML was ugly, so spent a few days and created
domain-specific language for specifying a reconciliation. Worked well, although creates some impedance - must change translator each time the requirements
change. However, it actually had the major benefit of helping to refine
requirements.
                                                                                
## Technical Issues                                                

Users' immediate reaction was they want a GUI, not the domain-specific language Ideal thing might
have been Eclipse plugin with syntax highlighting, etc., but would take too long to develop. So the compromise was a
wizard - quick to write - that generated the DSL code. Some discussion
about the potential of using Lisp or Smalltalk to create the DSL as part of the
language itself. The danger here is that users could do other things they
weren't expected to do. 