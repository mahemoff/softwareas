---
id: 97
title: 'Java Annotations Tutorial Notes &#8211; Benedict Heal at SPA 2005'
date: 2005-04-16T22:12:08+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=97
permalink: /java-annotations-tutorial-notes-benedict-heal-at-spa-2005/
dsq_thread_id:
  - "375488621"
  - "375488621"
categories:
  - SoftwareDev
---
Benedict overviewed the basics of Java annotations in a 75-minute tutorial. I was looking forward to this as I attended his [Tiger session](http://www.cix.co.uk/~bheal/java/java1.5/index.htm) last year and it was a spot-on summary of all the main points. This tutorial likewise.
                                                                                                                                                                
##Many different types of comments
                                          
Including:
                                      
* Historical info
* State of code (e.g. TODOs, bug notes)
* Behavioural expectations (assumptions)
* Environment requirements
* Algorithm descriptions.
                                                                                
##Annotations are a big step beyond Javadoc tags
                                                                                
Java already has some structured metadata (e.g.@deprecated tag), but
annotations let anyone create such structures. Exactly how they'll be used is
an open question, ideas are emerging. Some examples: say where help files are, what classes are
required, input assumptions. The sort of thing you might have previously stored
in XML files or simply written in prose comments and hoped someone would see
them.
                                                                                
##Annotations categorised according to associated info
                                                                                
###Marker annotations
                                                                                
We might have a "financial" annotation, which would be used to log all methods:
                                                                                
  @Financial public class Invoice
                                                                                
Or we might have a "test" annotation instead of JUnit's naming convention (See
TestNG):
                                                                                
  @TestMethod void testSomething();
                                                                                
###Beyond marker annotations
                                                                                
These are annotations with a parameter, e.g.:
                                                                                
  @Help(url="http://example.com/help")
                                                                                
Don't have to name the parameters - can use an array too. @Annotation(a,b,c)
                                                                                
Useful to use enums here - the value of a parameter can be an enum.
                                                                                
##Java 1.5 offers three built-in annotations
                                                                                
> @Override public String toSTRing(){} //Will complain because it's not overriding.
                                                                                
> @Deprecated public void oldMethod(){}
                                                                                
> @SuppressWarnings(value={"unchecked"}) class DubiousClass
                                                                                
## How to write an annotation?
                                                                                
Looks like an interface ...
                                                                                
> public @interface Security {
    String access() default "all";
  }
                                                                                
Note: Because its an interface, you can't have behaviour on it (unlike C#). But an interface is no good without some related code; otherwise it may as well just be a comment. Which leads to the question: where does the related behaviour go? There was some discussion here ... A useful idiom
is to sneak the class into the annotation as a default value. Or another trick would be to declare a constant class member.
                                                                                
## Annotation Targets: What type of thing does the annotation apply to? What's being annotated?
                                                                                
Annotations can declare what they apply to: packages, classes, methods,
attributes etc.  These are called "Annotation Targets". And can use @inherited
to ensure the annotation is inherited.
                                                                                
## Meta-Annotations: Annotations about Annotations
                                                                                
Meta-annotations are annotations about annotations. For instance, @Documented
marks whether to add the annotation to Javadoc. [Sounds overly complex for the
fun of it, but apparently proving quite useful.]
                                                                                
## Source, Classloader, Runtime: When and How is the Annotation Used?
                                                                                
Can transform **source**, can intercept **classloading**, can manipulate at
**runtime**.
                                                                                
* Source Code: Could write your own processor. But you can also use the
Annotation Processing Tool (APT) ships with Java 5. For an annotation,
implement an *AnnotationProcessor* which walks through source code, picks out
annotation types, and outputs the code accordingly. Annoyingly, APT doesn't let
you read the method code, so you can't do any manipulation there. Apparently,
that's a sticking point and will hopefully be resolved soon.
                                                                                
* Classloader: Could write your own classloader, but BCEL or Javassist are
tools that let you easily change classloading behaviour without doing so. To
manipulate the Loader, you implement a *Translater*. Can then add the code.
Apparently easier than you'd think (a toy example is actually very small).

* Runtime: Can ask a class/method/etc about its annotations. Could be used in
any way, as with regular reflection.
                                                                                
## Open Issues
                                                                                
How we use annotations is still something of a mystery, and we'll be learning a
lot as they start to be used. For instance, what's the point of a marker
annotation such as @TestMethod.  Isn't the name alone enough to tell us it's a
test method. When you see a call to a method, you see it's name but not the
annotation. 
                                  
AOP will benefit from a standard notation - the AOP/annotation combination may well be a good combo.

Some discussion here about how much they really offer, and is it enough given the
great drawback that there's a lot of *potential* extra complexity added. 
<the main consensus here is that most sane projects won't create their own
annotations. I guess it will become something akin to JSP taglibs or Ant contrib tasks
- apache and others will create well-known libraries, there will be some
domain-specific libraries, and Sun will eventually add a number of annotations
to J2SE.>

JSR 250 is specifying common annotations and RAPT - https://rapt.dev.java.net/ - is building a library of annotations.
</the>