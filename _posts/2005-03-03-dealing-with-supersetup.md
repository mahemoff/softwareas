---
id: 68
title: Refactoring from super.setUp()
date: 2005-03-03T02:24:58+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=68
permalink: /dealing-with-supersetup/
dsq_thread_id:
  - "375572175"
  - "375572175"
categories:
  - SoftwareDev
---
Cedric rightly points out that [JUnit's "Call super"](http://beust.com/weblog/archives/000252.html) is a serious antipattern. This happens a lot in my experience too - project-wide test classes that where any special setUp() must call super.setUp(). JUnit has served its purpose admirably, but I think there are now more effective test frameworks (I'd like to check out JBehave, TestNG, and Artima SuiteRunner), but widespread familiarity with the JUnit dictates that JUnit is often the de facto choice.

Encouraging or forcing people to call super is completely evil. It brings out the worst of  OO inheritance. What can go wrong? I'll use JUnit to illustrate, though the points relate to any OO architecture, not just JUnit or testing. These are the main problems:

* <b>The subclass author might forget to call super.setUp(), or might not be aware its necessary.</b>

* <b>super.setUp() might one day change behaviour</b>, so the assumptions of subclasses are no longer valid. The subclass may be using a variable that is no longer initialised, for instance.

* Now that we're using this "sometimes call super" pattern, subclass authors have to tread delicately ... <b>any non-final, non-private, method in the superclass is now in play</b> ... it's a candidate for calling super from the subclass. How about tearDown(). Do I have to call super.tearDown(). Only way to find out is to inspect the code, rely on documentation, or ask someone. Hopefully, it won't change. How about some of those protected utility methods that I'm allowed to override for greater granularity? Do I have to call super on them too?

<b>The best antidote is usually a template method.</b> That's the thing to do in the case of JUnit: 

<pre>
public class SpaceGameTest extends TestCase { // UNCOMPILED!

    public <b>final</b> void setUp() {

        createTeams(); // Example of project-wide setup
        <b>afterSpaceGameSetUp();</b>
    }

    protected abstract afterSpaceGameSetUp();

}

--

public class BattleTest extends TestCase {
    ...
    <b>public void afterSpaceGameSetUp() {
        score = 0;
    }</b>

}

</pre>

Great, the subclass author is now forced to override afterSpaceGameSetUp() and write setUp(). Immediate notification from your friend, AKA the compiler, if you forgot. And the method tells you exactly when it will occur in the test lifecycle.

BTW I'm not sure I agree with Cedric's idea on multiple calling setUpAnything()? What order would it call them in? Use reflection to call superclasses first, then subclasses, and so on down to the bottom? It would be a confusing violation of OO (even beyond that reasonably performed by JUnit for testing purposes). Or maybe alphabetical order, so you'd end up with a convention of setUp01Blah() ... but that would defeat the purpose of separating out base classes from subclasses. I'm fairly happy with the template class solution as it keeps the test framework model simple.

Also, if, for some reason, you insist on requiring super.setUp() ("industry standard" is one such reason, though I don't buy it), then it's worth easing the pain as follows:
* Declare anything "final" that you don't expect to be overridden. Makes it more obvious when you *do* need to override things.
* I strive to avoid comments where possible, but that's because I favour neat code and clean architecture over extensive documentation. Since the "call super" design is error-prone, this is one time where comments really are needed, so explain what needs to be done.
* Basic psychology suggests people will inevitably forget to call super. If the consequence is subtle, people will be frustrated as they spend time trying to work out what's gone wrong. Make the consequence slap in the face with an assertion: <b>in the base class, write a "final" test method that checks the assumptions set up by the base setUp() (create a flag variable if necessary, to test that base setUp() has been called)</b>.