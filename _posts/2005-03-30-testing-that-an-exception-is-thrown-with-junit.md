---
id: 82
title: Testing that an Exception is Thrown with JUnit
date: 2005-03-30T23:21:30+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=82
permalink: /testing-that-an-exception-is-thrown-with-junit/
categories:
  - SoftwareDev
---
<h3>How do you verify your component throws an exception?</h3>

Most tests verify something works. But exceptional cases are important too, and what do many exceptional cases do? Throw exceptions of course.

So how do you verify your component throws an exception?

<h3>Real possibilities</h3>

My favourite idiom for testing exceptions is:

<pre> <code>
    try {
        map.locateCoordinates("Alpha Centauri");
        fail();
    } catch(OutOfBoundsException ex) {}
</code></pre>

The code will *fail()* if the errant statement falls through to it; i.e. if the errant statement does not throw an exception.

Another idiom is:
<pre> <code>
    boolean exceptionThrown=false;
    try {
        map.locateCoordinates("Alpha Centauri");
    } catch(OutOfBoundsException ex) {
        exceptionThrown=true;
    }
    assertTrue(exceptionThrown);
</code></pre>

I prefer the former as it's more terse. Some may say it's less intuitive, but that's the whole point of idioms; they're a good thing because they compress code, and as long as you can internalise their meaning, you can recognise what's going on [in a blink](http://www.softwareas.com/index.php?p=65). In any event, they're variations on a theme.

A different approach is to encapsulate the exception-throwing code in a command interface:

<pre> <code>
    verifyExceptionThrown(new ExceptionThrowingCommand() {
        public void exceptionThrowingBlock() {
            map.locateCoordinates("Alpha Centauri");
        }
    }
    ...
    private void verifyExceptionThrown(ExceptionThrowningCommand command) {
    try {
        command.exceptionThrowingBlock();
        fail();
    } catch(OutOfBoundsException ex) {}
    }
</code></pre>

In this case, we've extracted out the idiom for verifying an exception is thrown. Unfortunately, it didn't do much good, because calling it - due to the  anonymous class declaration - is actually about as lengthy as doing the whole thing anyway! This approach does have the benefit of isolating the standard approach to exceptions, so you could for instance have a common error message. And it's probably less error-prone; hard to err in calling the *verify* method. Nonetheless, it adds an extra layer of abstraction, and extra layers of abstraction should not be added lightly. So I'm still sticking with the first version.

<h3>Fantasy-land possibilities</h3>

So much for reality, how tedious. Here's how I would like it to be done. If Java had closures - and CSharp's anonymous method shows it's feasible - you could call a verify method something like this:

<pre> <code>
    verifyExceptionThrown({map.locateCoordinates("Alpha Centauri")}); // I'm making up the syntax!
</code></pre>

More realistically, JUnit's reflection could quite easily be altered to let you declare a test method throws an exception:

<pre> <code>
    public void testGettingCoordinatesOfFarawayStarThrowsOutOfBoundsException() {
        map.locateCoordinates("Alpha Centauri")
    }
</code></pre>

This way, by merely following the common wisdom that test methods should be self-documenting, JUnit will be able to use reflection to check that what kind of exception is thrown.

Well, maybe [JBehave](http://jbehave.codehaus.org/) with its various hooks might be suited to this sort of thing.

<h3>Caveat: Sometimes You Want to Verify the Exception</h3>

Some of the above would need further modification if you are concerned about verifying details of the exception in the *catch* block, e.g.:
> assertTrue(ex.getMessage("Whew! That's a bit far, what are you gonna do? Teleport yourself?!"))

In practice, there's not too much value in doing that too often: messages are fragile, and even for other exception information, you possibly only want to check it once or twice. The rest of the time, you probably just want to know the right type of exception was thrown.<!--bb42268ea0c1ead483ffe568bad524c0-->